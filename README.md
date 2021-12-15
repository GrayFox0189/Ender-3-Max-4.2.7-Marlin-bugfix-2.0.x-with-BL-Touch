# Ender-3-Max-4.2.7-Marlin-bugfix-2.0.x-with-BL-Touch
Latest Marlin bugfix-2.0.x with Ender 3 Max with BL Touch

I changed these parameters to have the settings as close to the original as possible.

Thanks for the hint to Teaching Tech, holmes4 (from Creality Forum) and Flawioo (from GitHub)

List of Changes:

platform.ino

16    default_envs = STM32F103RET6_creality


Configuration.h

120   #define BAUDRATE 115200 // Change Baudrate from 250000 to 115200.

144   #define MOTHERBOARD BOARD_CREALITY_V427 // Choose right version of motherboard.

568   #define BED_MAXTEMP      120 // From 150 to 120.

593   #define PID_EDIT_MENU // Add PID editing to the "Advanced Settings" menu. (~700 bytes of PROGMEM).

594   #define PID_AUTOTUNE_MENU // Add PID auto-tuning to the "Advanced Settings" menu. (~250 bytes of PROGMEM).

724   #define EXTRUDE_MAXLENGTH 200 // From 500 to 200.

956   #define DEFAULT_MAX_ACCELERATION      { 500, 500, 100, 1000 } // From { 3000, 3000, 100, 10000 } to { 500, 500, 100, 1000 }.

1010  #define JUNCTION_DEVIATION_MM 0.08 // (mm) Distance from real junction edge // I have used the formula 0.4*DefJerk(10)*Defjerk(10)/DefAccel(500).

1023  //#define S_CURVE_ACCELERATION // Disable S_CURVE_ACCELERATION.

1042  #define USE_PROBE_FOR_Z_HOMING // ENABLE FOR BLTOUCH.

1059  #define Z_MIN_PROBE_PIN 17 // Pin 32 is the RAMPS default // Pin number correction for BL Touch.

1096  #define BLTOUCH // ENABLE FOR BLTOUCH.

1188  #define NOZZLE_TO_PROBE_OFFSET { 47, -13.5, -2.55 } // This value is suited for original BL Touch mount bracker change this value if you print your custom bracket.

1192 	#define PROBING_MARGIN 15 // From 10 to 15 for a little bit secure probing.

1248	#define MULTIPLE_PROBING 2 // Increase number of probing. Slower but accurate.

1418	//#define MIN_SOFTWARE_ENDSTOP_Z // DISABLE FOR BLTOUCH.

1555	#define AUTO_BED_LEVELING_BILINEAR  // ENABLE FOR BLTOUCH.

1686	#define LCD_BED_LEVELING // Added Bed Levelling Sub-Menu.

1875	#define PREHEAT_1_TEMP_HOTEND 200 // Changed for my material.

1876	#define PREHEAT_1_TEMP_BED     60 // Changed for my material.

1882	#define PREHEAT_2_TEMP_BED     70 // Changed for my material.

1901	#define NOZZLE_PARK_POINT { (X_MAX_POS - 10), (Y_MIN_POS + 10), 20 } // From { (X_MIN_POS + 10), (Y_MAX_POS - 10), 20 } this move hotend in front of the bed.


Configuration_adv.h

1272  #define PROBE_OFFSET_WIZARD // Add Probe Z Offset Wizard.

1950  #define BABYSTEP_ZPROBE_OFFSET          // Combine M851 Z and Babystepping // Enabled babystep for better accuracy.

1974  //#define LIN_ADVANCE // Disabled linear advance. I couldn't get it to work.

2472  #define FILAMENT_CHANGE_UNLOAD_FEEDRATE     10  // (mm/s) Unload filament feedrate. This can be pretty fast. // I wanted to have the original settings of my Ender 3

2474  #define FILAMENT_CHANGE_UNLOAD_LENGTH      100  // (mm) The length of filament for a complete unload.

2481  #define FILAMENT_CHANGE_FAST_LOAD_FEEDRATE   6  // (mm/s) Load filament feedrate. This can be pretty fast.

2483  #define FILAMENT_CHANGE_FAST_LOAD_LENGTH     0  // (mm) Load length of filament, from extruder gear to nozzle.

2488  #define ADVANCED_PAUSE_PURGE_LENGTH         50  // (mm) Length to extrude after loading.
