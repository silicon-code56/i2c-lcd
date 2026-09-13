# i2c-lcd
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Define LCD properties
const int lcd_columns = 16;
const int lcd_rows = 2;

// Initialize the LCD
LiquidCrystal_I2C lcd(0x27, lcd_columns, lcd_rows);

// Define the message to be scrolled
String message = " GOVERNMENT POLYTECHNIC AHMEDABAD";

void setup() {
  // Initialize the LCD
  lcd.init();
  lcd.backlight();

  // Set the cursor to the top-left corner
  lcd.setCursor(0, 0);
}

void loop() {
  // Loop through each character in the message
  for (int i = 0; i < message.length(); i++) {
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print(message.substring(i) + message.substring(0, i));
    delay(500);
  }
}

