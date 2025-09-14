# bmwista
BMW Ista+ Install

# Prerequisites

# Troubleshooting
 
# Execute Measures Plan is grayed out

## Steps

1. **Open Registry Editor**
   - Press **Win + R**, type `regedit`, and press **Enter`.
   - Approve the UAC prompt if asked.

2. **Navigate to the Parent Path**
   - Go to the key where you want this setting stored, for example:
     - `HKEY_LOCAL_MACHINE\SOFTWARE\BMWGroup\ISPI\Rheingold`
     - or (on 64-bit systems)  
       `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\BMWGroup\ISPI\Rheingold`
   - Confirm the correct location from ISTA documentation.

3. **Create the Key (if needed)**
   - In the left pane, right-click the parent folder → **New → Key**.
   - Name it:
     ```
     BMW.Rheingold.ISTAGUI
     ```

4. **Add the Value**
   - Select the `BMW.Rheingold.ISTAGUI` key.
   - In the right pane, right-click → **New → String Value**  
     *(or **DWORD (32-bit)** if ISTA expects `1`/`0` instead of `true`/`false`).*
   - Name it:
     ```
     enableENETprogramming
     ```
   - Double-click it and set the value data to:
     ```
     True
     ```

5. **Close Registry Editor**
   - Changes apply immediately.  
   - Restart ISTA or your PC if needed.
