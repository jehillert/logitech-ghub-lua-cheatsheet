### FLOW CONTROL
    function OnEvent(event, arg [, family]) | end
    if condition then | doThat | end
    if not condition then doThat | end
    for iter = 0, 10 do | doThat | end

### NUMBER: MOUSE_BUTTON
    1|LButton
    2|MButton
    3|RButton
    4|XButton1
    5|XButton2

### FUNCTIONS
    OnEvent(event, arg [, family]);
    EnablePrimaryMouseButtonEvents();
    PlayMacro("my macro");

### MOVE MOUSE CURSOR/WHEEL
    MoveMouseWheel(-1|1);       -- mouse wheel [-1|1] click down
    MoveMouseTo(0, 0)           -- mouse to upper left corner
    MoveMouseTo(32767, 32767)   -- mouse to center screen
    MoveMouseTo(65535, 65535)   -- mouse to lower right corner
    MoveMouseRelative(0, 0);    -- move [dx, dy] relative to current position
    MoveMouseToVirtual(0, 0);   -- mouse to absolute position on multi-monitor layout

### SET STATE
    SetBacklightColor((red, green, blue, [family]);
    SetMKeyState(mkey, [family]);
    SetMouseDPITable({value1, value2, value3}, [index]);
    SetMouseDPITable({500, 1000, 1500, 2000, 2500, ...16_entry_max})
    SetMouseDPITableIndex(1|2|3 ...16);
    Sleep( 20 );

### GET STATE
    "M1"|"M2"|"M3" = GetMKeyState(“kb”|"lhc")
    "M1"|"M2"|"M3" = GetMKeyState()
    x, y = GetMousePosition()
    t_ms = GetRunningTime();
    date = GetDate([format [, time]])

### LOGGING & DEBUGGING
    OutputDebugMessage("logs to Windows debugger");
    OutputLCDMessage("logs to LCD");
    OutputLogMessage('logs to script editor');
    AbortMacro();
    ClearLog();

### PRESS/RELEASE [mouse]
    PressAndReleaseMouseButton(1|2|3|4|5|6)
    PressMouseButton(1|2|3|4|5|6)
    ReleaseMouseButton(1|2|3|4|5|6)

 ### PRESS/RELEASE [keyboard]
    PressAndReleaseKey("a", "b", "c", ...)
    PressAndReleaseKey(1, 2, 4, ...)
    PressKey("a", "b", "c", ...)
    ReleaseKey("a", "b", ...)

### EVENTS
    “MOUSE_BUTTON_PRESSED”      1|2|3|4|5|6   LB|MB|RB|XB1|XB2
    “MOUSE_BUTTON_RELEASED”     1|2|3|4|5|6   LB|MB|RB|XB1|XB2
    "G_PRESSED"|"G_RELEASED"    1|2|3…18      G1|G2|G3…G18
    "M_PRESSED"|"M_RELEASED"    1|2|3         M1|M2|M3
    "PROFILE_ACTIVATED"         none          none
    "PROFILE_DEACTIVATED"       none          none

### BOOLEAN
    true|false = IsKeyLockOn();
    true|false = IsModifierPressed("lalt"|"ralt"|"alt")
    true|false = IsModifierPressed("lctrl", "rctrl", "ctrl"
    true|false = IsModifierPressed("lshift"|"rshift"|"shift")
    true|false = IsMouseButtonPressed( 1|2|3|4|5|6 )

 ══════════════════════════════════════════════════════════════════════════════

### OnEvent Function is mandatory.
    function OnEvent(event, arg)
      if (event == "PROFILE_ACTIVATED") then
        -- profile has been activated
      end
      if (event == "PROFILE_DEACTIVATED") then
        -- profile has been deactivated
      end
      if (event == "G_PRESSED" and arg == 1) then
        -- G1 has been pressed
      end
      if (event == "G_RELEASED" and arg == 1) then
        -- G1 has been released
      end
      if (event == "M_PRESSED" and arg == 1) then
        -- M1 has been pressed
      end
      if (event == "M_RELEASED" and arg == 1) then
        -- M1 has been released
      end
      if (event == "MOUSE_BUTTON_PRESSED" and arg == 6) then
        -- Mouse Button 6 has been pressed
      End
      if (event == "MOUSE_BUTTON_RELEASED" and arg == 6) then
        -- Mouse Button 6 has been released
      end
    end
═══════════════════════════════════════════════════════════════════

### Press a mouse button
    PressMouseButton(1)

    if IsMouseButtonPressed(1) then
      OutputLogMessage("Left mouse button is pressed.\n");
    end

### Release a mouse button so that it is no longer pressed
    ReleaseMouseButton(1)

    if not IsMouseButtonPressed(1) then
      OutputLogMessage("Left mouse button is not pressed.\n");
    end

### Press a specific modifier
    PressKey("lshift")

    if IsModifierPressed("shift") then
      OutputLogMessage("shift is pressed.\n");
    end

### Release the key so it is no longer pressed
    ReleaseKey("lshift")
    if not IsModifierPressed("shift") then
      OutputLogMessage("shift is not pressed.\n");
    end

### Log current date/time
   OutputLogMessage("Today’s date/time is: %s\n", GetDate())

### Set the current M Key state to M1 when G1 is pressed
   function OnEvent(event, arg)
     if (event == "G_PRESSED" and arg == 1) then
       SetMkeyState(1);
     end
   end



----------------------------------------------
'escape'
'pause', 'tilde'
'printscreen', 'scrolllock',
'minus', 'equal', 'backspace', 'tab'
----------------------------------------------
'numenter', 'numperiod',
'numplus', 'numminus',
----------------------------------------------
'num0', 'num1', 'num2', 'num3', 'num4',
'num5', 'num6', 'num7', 'num8', 'num9'
----------------------------------------------
'f1','f2','f3','f4','f5','f6',
'f7','f8', 'f9', 'f10','f11',
'f12','f13', 'f14','f15', 'f16',
'f17', 'f18','f19','f20','f21',
'f22', 'f23', 'f24'
----------------------------------------------
'q', 'w', 'e', 'r', 't', 'y'
----------------------------------------------
'1', '2', '3', '4', '5', '6',
'7', '8', '9', 0

═══════════════════════════════════════════════════════════════════
**String Functions**

--- | --- | ---
string.byte | string.len
string.char | string.lower
string.dump | string.match
string.find | string.rep
string.format | string.reverse
string.gmatch | string.sub
string.gsub | string.upper

table.concat
table.insert
table.maxn
table.remove
table.sort
math.abs
math.acos
math.asin
math.atan
math.atan2
math.ceil
math.cos
math.deg
math.exp
math.floor
math.fmod
math.frexp
math.huge
math.ldexp
math.log
math.log10
math.max
math.min
math.modf
math.pi
math.pow
math.rad
math.random
math.randomseed
math.sin
math.sinh
math.sqrt
math.tan
math.tanh

═══════════════════════════════════════════════════════════════════

NOTE_1:
    -- Left Mouse Button (1) is not reported by default.
    -- Use ‘EnablePrimaryMouseButtonEvents’ to override this.
