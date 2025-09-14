# BMW ISTA (Integrated Service Technical Application)

BMW **ISTA** stands for **Integrated Service Technical Application**.  
It is BMW’s official diagnostic and service software used by dealerships and independent workshops for working on **BMW**, **MINI**, and **Rolls-Royce** vehicles.  

---

## What ISTA Does
- **Diagnostics**: Reads and clears fault codes (DTCs) from all vehicle control units (engine, transmission, ABS, airbag, etc.).
- **Programming & Coding**: Updates or reprograms vehicle control modules with factory software (requires special hardware or licenses).
- **Service Functions**: Provides guided procedures for maintenance and repairs (e.g., bleeding brakes, resetting adaptations, battery registration).
- **Wiring Diagrams & Technical Info**: Includes repair instructions, wiring diagrams, and troubleshooting guides directly from BMW.
- **Vehicle Identification**: Automatically detects the vehicle by VIN and retrieves build data and options.

---

## Components
- **ISTA/D (Diagnostics)**: Focused on troubleshooting, reading data, and performing service functions.
- **ISTA/P (Programming)**: Used for software updates and programming modules (on older setups; newer ISTA integrates both).

---

## Who Uses It
- BMW dealerships (official software).
- Independent BMW specialists with proper hardware and access.
- Advanced enthusiasts who want dealer-level diagnostics.  
  *Note: Full programming functions usually require BMW’s ICOM interface and a stable power supply.*

---

👉 In short: **ISTA is BMW’s “dealer tool” for diagnostics, coding, and repair guidance**, similar to:
- **VW/Audi** → ODIS  
- **Mercedes** → Xentry


# Prerequisites

System requirements for ISTA 4.21.3x and higher:

1. Windows 10 v1903 or higher
2. Microsoft .NET Framework 4.8.x
3. Visual C++ Runtime 2015-2019 (both x64 and x86)
4. Google Chrome browser
5. Windows username should not contain spaces, dashes and special characters like "ö".

***Windows 7/8 not supported***

***Internet Explorer and EDGE not ssupported***

# Troubleshooting

## Error is received when connecting to vehicle

If running Windows 11 ensure you have Microsoft Visual C++ Redistributable x86 and x64 installed.

[https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#:~:text=of%20the%20redist.-,Latest%20Microsoft%20Visual%20C%2B%2B%20Redistributable%20version,-The%20latest%20version)
 
## Execute Measures Plan is grayed out

### Steps

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
