我编程了一个oled屏幕单行或多行输出的程序，大家可以拿去使用！
只支持英文！不支持中文！
此文件能在mind+打开。mind+官网：https://mindplus.cc/
如需使用IDE编程的话，请使用mind+生成的代码，代码如下：
```
/*!
 * MindPlus
 * uno
 *
 */
#include <DFString.h>
#include <DFRobot_SSD1306_I2C.h>

// 动态变量
volatile float mind_n_YiXunHuanCiShu;
// 函数声明
void DF_XunHuanXianShi(String mind_s_string);
void DF_DuoXingXunHuanGunDongXianShi(String mind_s_string);
// 创建对象
DFRobot_SSD1306_I2C oled12864;


// 主程序开始
void setup() {
	oled12864.begin(0x3c);
	DF_DuoXingXunHuanGunDongXianShi("When you learn a foreign language,you must learn more than the vocabulary and the grammar. To communicate successfully, you must also learn the non-verbal language, or “body language”of that culture. “Body language” is a term used to describe facial expression,gestures, and other movements of the body that send messages. This means of communication is so important that we may actually say more with our movements than with words.");
}
void loop() {

}

// 自定义函数
void DF_XunHuanXianShi(String mind_s_string) {
	oled12864.fillScreen(0);
	if (((String(mind_s_string).length())<=16)) {
		oled12864.setCursorLine(1);
		oled12864.printLine(mind_s_string);
	}
	else {
		mind_n_YiXunHuanCiShu = 0;
		while (1) {
			for (int index = 0; index < (String(mind_s_string).length()); index++) {
				mind_n_YiXunHuanCiShu += 1;
				oled12864.setCursorLine(1);
				oled12864.printLine((dfstring.substring(mind_s_string,0,mind_n_YiXunHuanCiShu,0,(mind_n_YiXunHuanCiShu + 15))));
				delay(400);
			}
			mind_n_YiXunHuanCiShu = 0;
			oled12864.fillScreen(0);
		}
	}
}
void DF_DuoXingXunHuanGunDongXianShi(String mind_s_string) {
	if (((String(mind_s_string).length())<=16)) {
		oled12864.setCursorLine(1);
		oled12864.printLine(mind_s_string);
	}
	else if (((String(mind_s_string).length())<=32)) {
		oled12864.setCursorLine(1);
		oled12864.printLine((dfstring.substring(mind_s_string,0,1,0,16)));
		oled12864.setCursorLine(2);
		oled12864.printLine((dfstring.substring(mind_s_string,0,17,0,32)));
	}
	else if (((String(mind_s_string).length())<=48)) {
		oled12864.setCursorLine(1);
		oled12864.printLine((dfstring.substring(mind_s_string,0,1,0,16)));
		oled12864.setCursorLine(2);
		oled12864.printLine((dfstring.substring(mind_s_string,0,17,0,32)));
		oled12864.setCursorLine(3);
		oled12864.printLine((dfstring.substring(mind_s_string,0,33,0,48)));
	}
	else if (((String(mind_s_string).length())<=64)) {
		oled12864.setCursorLine(1);
		oled12864.printLine((dfstring.substring(mind_s_string,0,1,0,16)));
		oled12864.setCursorLine(2);
		oled12864.printLine((dfstring.substring(mind_s_string,0,17,0,32)));
		oled12864.setCursorLine(3);
		oled12864.printLine((dfstring.substring(mind_s_string,0,33,0,48)));
		oled12864.setCursorLine(4);
		oled12864.printLine((dfstring.substring(mind_s_string,0,49,0,64)));
	}
	else {
		mind_n_YiXunHuanCiShu = 0;
		while (1) {
			for (int index = 0; index < ((floor((((String(mind_s_string).length()) - 64) / 16))) + 5); index++) {
				mind_n_YiXunHuanCiShu += 1;
				oled12864.setCursorLine(1);
				oled12864.printLine((dfstring.substring(mind_s_string,0,((mind_n_YiXunHuanCiShu * 16) - 15),0,(mind_n_YiXunHuanCiShu * 16))));
				oled12864.setCursorLine(2);
				oled12864.printLine((dfstring.substring(mind_s_string,0,(((mind_n_YiXunHuanCiShu * 16) - 15) + 16),0,((mind_n_YiXunHuanCiShu * 16) + 16))));
				oled12864.setCursorLine(3);
				oled12864.printLine((dfstring.substring(mind_s_string,0,(((mind_n_YiXunHuanCiShu * 16) - 15) + 32),0,((mind_n_YiXunHuanCiShu * 16) + 32))));
				oled12864.setCursorLine(4);
				oled12864.printLine((dfstring.substring(mind_s_string,0,(((mind_n_YiXunHuanCiShu * 16) - 15) + 48),0,((mind_n_YiXunHuanCiShu * 16) + 48))));
				delay(1500);
			}
			mind_n_YiXunHuanCiShu = 0;
			oled12864.fillScreen(0);
		}
	}
}
```
