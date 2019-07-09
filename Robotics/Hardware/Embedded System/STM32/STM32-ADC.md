---
title: STM32-ADC
author: Junhan Hu
tags:
  - STM32
  - ADC
mathjax: true
categories:
  - Robotics
  - Hardware
  - Embedded System
  - STM32
date: 2018-12-27 00:00:00
---



## 1 Introduction

STM32 have one of the most advanced ADCs on microcontroller market.

This note provide users to understand some modes offered in STM32

<!-- more -->

## 2 Independent Mode

* Single Channel, **single** conversion

  Example:  Check if the battery voltage is succulent or not

  ![single-conversion](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/single-conversion.png)

* Multichannel, single conversion

  Example:  Can be used when starting system depends on some **parameters**

* Single Channel, continuous conversion

  Example: Run in **background**, so can be used as a monitor to check something all the time

  ![continuous-conversion](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/continuous-conversion.png)

* Injected conversion

  Intended for use when conversion is triggered by an **external event** or by software.

  ![Injected-conversion](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/Injected-conversion.png)


## 3 Example Code

```c
void GPIOINIT_ADC()
{
	GPIO_InitTypeDef GPIO_InitStructure;
	GPIO_InitStructure.GPIO_Pin=GPIO_Pin_0;//ADC
	GPIO_InitStructure.GPIO_Mode=GPIO_Mode_AIN;	//模拟输入
	GPIO_InitStructure.GPIO_Speed=GPIO_Speed_50MHz;
	GPIO_Init(GPIOB,&GPIO_InitStructure);

}
void RCCINIT_ADC()
{
	SystemInit();
	RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOB,ENABLE);
	RCC_APB2PeriphClockCmd(RCC_APB2Periph_AFIO,ENABLE);
	RCC_APB2PeriphClockCmd(RCC_APB2Periph_ADC1,ENABLE);
	RCC_ADCCLKConfig(RCC_PCLK2_Div6);//12M  最大14M 设置ADC时钟（ADCCLK）
}
void ADCINIT_ADC()
{

	ADC_InitTypeDef ADC_InitStructure;
	ADC_InitStructure.ADC_Mode = ADC_Mode_Independent; 
	ADC_InitStructure.ADC_ScanConvMode = DISABLE; 
	ADC_InitStructure.ADC_ContinuousConvMode = DISABLE; 
	ADC_InitStructure.ADC_ExternalTrigConv = ADC_ExternalTrigConv_None; 
	ADC_InitStructure.ADC_DataAlign = ADC_DataAlign_Right; 
	ADC_InitStructure.ADC_NbrOfChannel = 1; 
	ADC_Init(ADC1, &ADC_InitStructure);
	ADC_TempSensorVrefintCmd(ENABLE);
	ADC_Cmd(ADC1,ENABLE);	

	ADC_ResetCalibration(ADC1);//重置指定的ADC的校准寄存器
	while(ADC_GetResetCalibrationStatus(ADC1));//获取ADC重置校准寄存器的状态
	
	ADC_StartCalibration(ADC1);//开始指定ADC的校准状态
	while(ADC_GetCalibrationStatus(ADC1));//获取指定ADC的校准程序
	ADC_RegularChannelConfig(ADC1,ADC_Channel_8,1,ADC_SampleTime_239Cycles5);//设置指定ADC的规则组通道，设置它们的转化顺序和采样时间
	ADC_SoftwareStartConvCmd(ADC1, ENABLE);//使能或者失能指定的ADC的软件转换启动功能
	while(ADC_GetFlagStatus(ADC1, ADC_FLAG_EOC) == RESET);

}
```

