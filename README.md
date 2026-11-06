# STM32 - ADS1115 Single-Ended, Single-Shot, PGA & Data Rate Enabled HAL Library 
A simple C library (STM32 HAL) for single-ended single-shot ADC measurments with ADS1115 module. (Tested on STM32F411RE)

⚠️ Note: This is a community-maintained fork of the original ADS1115 library by Ahmet Batuhan Günaltay (2021). The original repository has been inactive for over 2 years. This fork adds detailed I2C error codes, a HAL compatibility wrapper, and improved debugging support for STM32F4. Licensed under GPL v3.

This library includes several configurations such as PGA and data rate of ADS1115 and tested on STM32F411RE. Example project available.

* ! I2C_ADS1115_readOneShot(...) returns voltage as mV.

* Don't forget to check datasheet of ADS111x for detailed information: https://www.ti.com/lit/gpn/ADS1113
* Don't forget to check ads1115.h file.

## Example Usage
Configure an I2C peripheral on CubeMX.

```c

/* USER CODE BEGIN 2 */

  // ADS1115 Init
  if(I2C_ADS1115_Init(&hi2c1, ADS1115_DATA_RATE_64, ADS1115_PGA_ONE) == HAL_OK){
	  // Device found.
	  HAL_Delay(1500);
  } else{
	  // Device cannot found.
	  while(1);
  }

  float voltageRead;

/* USER CODE END 2 */

```
And,
```c
 /* USER CODE BEGIN WHILE */
float adc_voltage = 0.0f;

  while (1)
  {

	if(I2C_ADS1115_StartContinuous(ADS1115_MUX_AIN0, &adc_voltage) == HAL_OK){
		//Voltage successfully read.
	 }

 /* USER CODE END WHILE */
```

## [Türkçe/Turkish] Kullanım Talimatı

 * Adress değişkenini güncelleyin:
 	1) ADDR PIN --> GND ise 1001000
 	2) ADDR PIN --> VDD ise 1001001
 	3) ADDR PIN --> SDA ise 1001010
 	4) ADDR PIN --> SCL ise 1001011

