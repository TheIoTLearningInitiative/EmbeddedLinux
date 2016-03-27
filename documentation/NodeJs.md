NodeJS
==

- [Principles of Writing Consistent, Idiomatic JavaScript](https://github.com/rwaldron/idiomatic.js)
- [A set of node-red nodes for connecting to johnny-five IO Plugins](https://github.com/monteslu/node-red-contrib-gpio)
- [Intel Galileo & Intel Edison IO Plugin for Johnny-Five](https://github.com/rwaldron/galileo-io/)

var mraa = require('mraa');
var pinDigital = new mraa.Gpio(13);

console.log('MRAA Version: ' + m.getVersion());

pinDigital.dir(mraa.DIR_OUT);
pinDigital.write(1);


```sh
root@edison:~# ls /usr/lib/node_modules/
iotkit                    jsupm_grovevdiv           jsupm_mpl3115a2
iotkit-agent              jsupm_grovewater          jsupm_mpr121
iotkit-comm               jsupm_grovewfs            jsupm_mpu9150
jsupm_a110x               jsupm_guvas12d            jsupm_mq303a
jsupm_ad8232              jsupm_h3lis331dl          jsupm_my9221
jsupm_adafruitms1438      jsupm_hcsr04              jsupm_nrf24l01
jsupm_adafruitss          jsupm_hm11                jsupm_nrf8001
jsupm_adc121c021          jsupm_hmc5883l            jsupm_nunchuck
jsupm_adis16448           jsupm_hmtrp               jsupm_otp538u
jsupm_adxl335             jsupm_hp20x               jsupm_pca9685
jsupm_adxl345             jsupm_ht9170              jsupm_pn532
jsupm_am2315              jsupm_htu21d              jsupm_ppd42ns
jsupm_apds9002            jsupm_hx711               jsupm_pulsensor
jsupm_at42qt1070          jsupm_i2clcd              jsupm_rfr359f
jsupm_biss0001            jsupm_ina132              jsupm_rgbringcoder
jsupm_bmpx8x              jsupm_isd1820             jsupm_rotaryencoder
jsupm_buzzer              jsupm_itg3200             jsupm_rpr220
jsupm_cjq4435             jsupm_joystick12          jsupm_servo
jsupm_ds1307              jsupm_l298                jsupm_si114x
jsupm_ecs1030             jsupm_ldt0028             jsupm_sm130
jsupm_enc03r              jsupm_lm35                jsupm_st7735
jsupm_flex                jsupm_lol                 jsupm_stepmotor
jsupm_gas                 jsupm_loudness            jsupm_sx6119
jsupm_gp2y0a              jsupm_lpd8806             jsupm_ta12200
jsupm_grove               jsupm_lsm303              jsupm_tcs3414cs
jsupm_grovecircularled    jsupm_lsm9ds0             jsupm_th02
jsupm_grovecollision      jsupm_m24lr64e            jsupm_tm1637
jsupm_groveehr            jsupm_max31723            jsupm_tsl2561
jsupm_groveeldriver       jsupm_max31855            jsupm_ttp223
jsupm_groveelectromagnet  jsupm_max44000            jsupm_ublox6
jsupm_groveemg            jsupm_max5487             jsupm_uln200xa
jsupm_grovegprs           jsupm_maxds3231m          jsupm_waterlevel
jsupm_grovegsr            jsupm_maxsonarez          jsupm_wheelencoder
jsupm_grovelinefinder     jsupm_mg811               jsupm_wt5001
jsupm_grovemd             jsupm_mhz16               jsupm_yg1006
jsupm_grovemoisture       jsupm_mic                 jsupm_zfm20
jsupm_groveo2             jsupm_mlx90614            mraa
jsupm_grovescam           jsupm_mma7455             npm
jsupm_grovespeaker        jsupm_mma7660
root@edison:~# 
```
