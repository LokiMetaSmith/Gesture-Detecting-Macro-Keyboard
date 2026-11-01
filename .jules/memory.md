## Archived: 2026-10-31

### Repository Context: Gesture Detection Macro Keyboard
*   **Project Overview**: A custom Bluetooth macro keyboard that uses machine learning (TensorFlow Lite for Microcontrollers) to detect gestures, running on an ESP32.
*   **Hardware Components**:
    *   Capacitive touch pad for drawing gestures.
    *   Capacitive touch bar for volume control.
    *   11 tactile buttons (Switch 11 is used for BLE pairing and OLED menu navigation).
    *   OLED display providing info like crypto prices, Bluetooth status, IP address, and ML predictions.
    *   Utilizes Trill capacitive sensors for touch.
*   **Software & Functionality**:
    *   Functions as a BLE HID device (appears as a keyboard to the host).
    *   Uses an AutoHotkey script (`hotkeys/hotkey_handler.ahk`) on the host to translate combinations/gestures into specific actions (e.g., git commands, media controls, window management).
*   **Machine Learning Pipeline**:
    *   Employs TensorFlow Lite to classify gestures from the touch pad (mapped to a 28x28 2D matrix).
    *   Scripts in `/training` handle the ML lifecycle: `collect_train_data.py` (via UART in training mode), `train_model.py`, and `test_model.py`.
    *   Training output (`gesture_model_tflite.c/.h`) is automatically generated and integrated into the ESP-IDF build.
    *   Supports a `--center_gesture` flag for translation-invariant gesture recognition.
*   **Firmware Build**:
    *   Built using the Espressif ESP-IDF framework (tested on v4.2) using standard `idf.py build` commands.
*   **Mechanical Design**:
    *   Full Fusion 360 CAD project files are stored in the `CAD/` directory.
