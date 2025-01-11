# VIPAS-CAVOLO-PROJECT
VIPAS cavolo project github repository (for model VP100s.) detailed information will be found here.


# description 

The VIPAS cavolo VP100 (shortened to Cavolo) is a BadUSB type device operating on a small microcontroller with the Arduino Leonardo program installed. A BadUSB is a device that can act as a HID (Human Interface Device). common examples of HIDs are keyboards, computer mouse, touchscreen, etc. 
These are devices suppose to be used by people to interact with their device, and the Cavolo acts like one. It is programmed using the Arduino IDE software with code developed by VIPAS. The default program simply uses short cuts on most desktop devices such as PCs and laptops to close all current open and running tabs.

# code

The Cavolo VP100 source code is listed below, feel free to change it to your liking using the Arduino IDE software: https://www.arduino.cc/en/software


#include <Keyboard.h>

const int buttonPin = 3; // Pin where the button is connected
unsigned long startTime; // Track the start time for the 2-second delay
bool buttonPressed = false; // To track the button state

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Set the button pin as input with an internal pull-up resistor
  Keyboard.begin(); // Initialize the Keyboard library
  startTime = millis(); // Record the start time
}

void loop() {
  // Check if the button is pressed
  if (digitalRead(buttonPin) == LOW && !buttonPressed) { // Button pressed (LOW state)
    buttonPressed = true; // Mark the button as pressed
    openTextEditMac(); // Execute the macOS-specific function
    startTime = millis(); // Reset the timer when the button is pressed
  }

  // Check if 2 seconds have passed without the button being pressed
  if (millis() - startTime > 2000 && !buttonPressed) {
    spamCloseTabsAndSearch(); // Execute the spam close tabs and search action
    startTime = millis(); // Reset the timer after action
  }

  // Reset the button state if the button is released
  if (digitalRead(buttonPin) == HIGH && buttonPressed) {
    buttonPressed = false; // Mark the button as released
    startTime = millis(); // Reset the timer
  }

  delay(50); // Add a short delay to stabilize readings
}

// Function to spam close tabs and open search bar
void spamCloseTabsAndSearch() {
  // ---- Windows - Close Tabs and Open Search ----
  for (int i = 0; i < 20; i++) {
    Keyboard.press(KEY_LEFT_CTRL);  // Ctrl key (Windows)
    Keyboard.press('w');           // W key (Close tab)
    delay(200);                    // Small delay between key presses
    Keyboard.releaseAll();         // Release all keys
    delay(200);                    // Short delay to simulate key hold time
  }

  delay(1000); // Pause before opening the search bar
  Keyboard.press(KEY_LEFT_GUI);  // Windows key
  Keyboard.press('s');           // S key (Search bar)
  delay(500);
  Keyboard.releaseAll();
  Keyboard.print("VIPAS CAVOLO VP 100"); // Type the message
  delay(1000);

  delay(3000); // Wait before switching to macOS

  // ---- macOS - Close Tabs and Open Spotlight Search ----
  for (int i = 0; i < 20; i++) {
    Keyboard.press(KEY_LEFT_GUI);  // Command key (macOS)
    Keyboard.press('w');           // W key (Close tab)
    delay(200);
    Keyboard.releaseAll();
    delay(200);
  }

  delay(1000); // Pause before opening Spotlight
  Keyboard.press(KEY_LEFT_GUI);  // Command key
  Keyboard.press(' ');           // Space key (Spotlight)
  delay(500);
  Keyboard.releaseAll();
  Keyboard.print("VIPAS CAVOLO VP 100"); // Type the message
  delay(1000);
}

// Function to open TextEdit and type in a message
void openTextEditMac() {
  Keyboard.press(KEY_LEFT_GUI); // Hold Command key
  Keyboard.press(' ');          // Press Space to open Spotlight
  Keyboard.releaseAll();
  delay(500);
  Keyboard.print("TextEdit");
  delay(500); // Allow time for TextEdit to appear in Spotlight
  Keyboard.press(KEY_RETURN);
  Keyboard.releaseAll();
  delay(1000); // Wait for TextEdit to open
  Keyboard.press(KEY_LEFT_GUI);
  Keyboard.press('n'); // New document
  Keyboard.releaseAll();
  delay(500);
  Keyboard.print("VIPAS CAVOLO PROJECT ADMIN PAGE. To customize this Cavolo VP100 BadUSB system, a text file will be downloaded soon.");
  delay(800);

  Keyboard.press(KEY_LEFT_GUI);
  Keyboard.press(' ');
  Keyboard.releaseAll();
  delay(500);
  Keyboard.print("Terminal");
  delay(500); // Allow time for Terminal to appear in Spotlight
  Keyboard.press(KEY_RETURN);
  Keyboard.releaseAll();
  delay(3000); // Wait for Terminal to open
  Keyboard.print("curl -O https://raw.githubusercontent.com/vipasrf/VIPAS-CAVOLO-PROJECT/refs/heads/main/CavoloVP100.md");
  delay(400);
  Keyboard.press(KEY_RETURN);
  Keyboard.releaseAll();
  delay(5000); // Wait for the file to download
  Keyboard.print("nano CavoloVP100.md");
  delay(500); // Allow time for nano to open the file
  Keyboard.press(KEY_RETURN);
  Keyboard.releaseAll();
  delay(500); // Wait for nano to open the file
  Keyboard.print("PLEASE GO TO: https://github.com/vipasrf/VIPAS-CAVOLO-PROJECT FOR FURTHER INFORMATION. BELOW IS THE SOURCE CODE.");
}



The program is written in a customized version of the C++ programming language. If you have expertise in it you can easily change around some of the actions within the code. For those who don't, it may take around 3-5 months to get a good hang of it. If you do not want to learn it, Github and other sites have endless amounts of code you can copy and paste. Within this reposistory there are example codes popular with BadUSB devices you may try out. 

