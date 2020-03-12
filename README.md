### FLOW CONTROL [FN1]
```lua
function OnEvent(event, arg [, family])
  doStuff
end
```
```lua
if condition then
  doStuff
end
```
```lua
if not condition then
    doStuff
end
```
```lua
for iter = 0, 10 do
    doStuff
end
```

### Mouse Buttons Integer Desigations
    1 | LButton [FN2]
    2 | MButton
    3 | RButton
    4 | XButton1
    5 | XButton2

### MISC FUNCTIONS
* `OnEvent(`event, arg [, family]`)`;
* `EnablePrimaryMouseButtonEvent(`true|false`)`;
* `PlayMacro(`"my macro"`)`;

### MOVE MOUSE CURSOR/WHEEL
* `MoveMouseWheel(`-1|1`)`;        -- mouse wheel [-1|1] click down
* `MoveMouseTo(`0, 0`)`;           -- mouse to upper left corner
* `MoveMouseTo(`32767, 32767`)`;   -- mouse to center screen
* `MoveMouseTo(`65535, 65535`)`;   -- mouse to lower right corner
* `MoveMouseRelative(`0, 0`)`;     -- move [dx, dy] relative to current position
* `MoveMouseToVirtual(`0, 0`)`;   -- mouse to absolute position on multi-monitor layout


### SET STATE
```lua
    SetBacklightColor((red, green, blue, [family]);
    SetMKeyState(mkey, [family]);
    SetMouseDPITable({value1, value2, value3}, [index]);
    SetMouseDPITable({500, 1000, 1500, 2000, 2500, ...16_entry_max})
    SetMouseDPITableIndex(1|2|3 ...16);
    Sleep( 20 );
```
### GET STATE
```lua
-- ——————————————————————————————————————————————————————————————————————————————————————
    GetDate() • GetMousePosition() •  GetRunningTime() • GetKeyState() • GetMKeyState()
-- ——————————————————————————————————————————————————————————————————————————————————————

    date = GetDate([format [, time]])

    x, y = GetMousePosition()
    t_ms = GetRunningTime();

    "M1"|"M2"|"M3" = GetMKeyState(“kb”|"lhc")
    "M1"|"M2"|"M3" = GetMKeyState()
```
### LOGGING & DEBUGGING
```lua
    OutputDebugMessage("logs to Windows debugger");
    OutputLCDMessage("logs to LCD");
    OutputLogMessage('logs to script editor');
    AbortMacro();
    ClearLog();
```
### PRESS/RELEASE [mouse]
```lua
    PressAndReleaseMouseButton(1|2|3|4|5|6)
    PressMouseButton(1|2|3|4|5|6)
    ReleaseMouseButton(1|2|3|4|5|6)
```
 ### PRESS/RELEASE [keyboard]
```lua
 -- keynames
    PressAndReleaseKey("a", "b", "c", ...)
    PressKey("a", "b", "c", ...)
    ReleaseKey("a", "b", ...)

 -- scancodes
    PressAndReleaseKey(1, 2, 4, ...)
    PressKey(1, 2, 3 ...)
```
### EVENTS

    “MOUSE_BUTTON_PRESSED”      1|2|3|4|5|6   LB|MB|RB|XB1|XB2
    “MOUSE_BUTTON_RELEASED”     1|2|3|4|5|6   LB|MB|RB|XB1|XB2
    "G_PRESSED"|"G_RELEASED"    1|2|3…18      G1|G2|G3…G18
    "M_PRESSED"|"M_RELEASED"    1|2|3         M1|M2|M3
    "PROFILE_ACTIVATED"         none          none
    "PROFILE_DEACTIVATED"       none          none

### BOOLEAN
```lua
    true|false = IsKeyLockOn();
    true|false = IsModifierPressed("lalt"|"ralt"|"alt")
    true|false = IsModifierPressed("lctrl", "rctrl", "ctrl"
    true|false = IsModifierPressed("lshift"|"rshift"|"shift")
    true|false = IsMouseButtonPressed( 1|2|3|4|5|6 )
```
 ---
### OnEvent Function is mandatory.
```lua
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
```
---
### _Press a mouse button:_
```lua
    PressMouseButton(1)

    if IsMouseButtonPressed(1) then
      OutputLogMessage("Left mouse button is pressed.\n");
    end
```
### _Release a mouse button so that it is no longer pressed:_
```lua
    ReleaseMouseButton(1)

    if not IsMouseButtonPressed(1) then
      OutputLogMessage("Left mouse button is not pressed.\n");
    end
```
### _Press a specific modifier:_
```lua
    PressKey("lshift")

    if IsModifierPressed("shift") then
      OutputLogMessage("shift is pressed.\n");
    end
```
### _Release the key so it is no longer pressed:_
```lua
    ReleaseKey("lshift")
    if not IsModifierPressed("shift") then
      OutputLogMessage("shift is not pressed.\n");
    end
```
### _Log current date/time:_
```lua
   OutputLogMessage("Today’s date/time is: %s\n", GetDate())
```
### _Set the current M Key state to M1 when G1 is pressed:_
```lua
  function OnEvent(event, arg)
     if (event == "G_PRESSED" and arg == 1) then
       SetMkeyState(1);
     end
   end
```
## KeyNames
---

&emsp;&emsp;escape&emsp;&emsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pause&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;&nbsp;tilde<br>
&emsp;&emsp;printscreen&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scrolllock&emsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;minus<br>
&emsp;&emsp;equal&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;&nbsp;backspace&emsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tab<br>

---
&emsp;&emsp;numenter&emsp;&emsp;&nbsp;&nbsp;numperiod<br>
&emsp;&emsp;numplus&emsp;&emsp;&emsp;numminus<br>

---
&nbsp;&emsp;&emsp;num1&emsp;&emsp;&emsp;&emsp;num2&emsp;&emsp;&emsp;&emsp;num3<br>
&nbsp;&emsp;&emsp;num4&emsp;&emsp;&emsp;&emsp;num5&emsp;&emsp;&emsp;&emsp;num6 <br>
&nbsp;&emsp;&emsp;num7&emsp;&emsp;&emsp;&emsp;num8&emsp;&emsp;&emsp;&emsp;num<br>
&nbsp;&emsp;&emsp;num0 <br>


---
&nbsp;&emsp;&emsp;f1&emsp;&emsp;&nbsp;f2&emsp;&emsp;&nbsp;&nbsp;&nbsp;f3&emsp;&emsp;&nbsp;&nbsp;f4&emsp;&emsp;&nbsp;&nbsp;f5&emsp;&emsp;&nbsp;&nbsp;f6&emsp;&emsp;<br>
&nbsp;&emsp;&emsp;f7&emsp;&emsp;&nbsp;f8&emsp;&emsp;&nbsp;&nbsp;&nbsp;f9&emsp;&emsp;&nbsp;&nbsp;f10&emsp;&emsp;f11&emsp;&emsp;f12&emsp;&emsp;<br>
&nbsp;&emsp;&emsp;f13&emsp;&emsp;f14&emsp;&emsp;f15&emsp;&emsp;f16&emsp;&emsp;f17&emsp;&emsp;f18<br>
&nbsp;&emsp;&emsp;f19&emsp;&emsp;f20&emsp;&emsp;f21&emsp;&emsp;f22&emsp;&emsp;f23&emsp;&emsp;f24<br>

---
&emsp;&emsp;1&emsp;2&emsp;3&emsp;4&emsp;5&emsp;6&emsp;7&emsp;8&emsp;9&emsp;0

---
&emsp;&emsp;q&emsp;w&emsp;e&emsp;r&emsp;t&emsp;y



|String Functions|<!-- -->|
|-------------|-------------|
|<ul>string.byte<br>string.char<br>string.dump<br>string.find<br>string.format<br>string.gmatch<br>string.gsub</ul>|<ul>string.len<br>string.lower<br>string.match<br>string.rep<br>string.reverse<br>string.sub<br> string.upper</ul>|
<p>

|Table Functions| <!-- -->|
|-------------|-------------|
|<ul>table.concat<br>table.inserttable.maxn</ul>|<ul>table.remove<br>table.sort</ul>|
<p>



|Math Functions| <!-- -->    | <!-- -->    |
|-------------|-------------|-------------|
|<ul>math.abs<br>math.acos<br>math.asin<br>math.atan<br>math.atan2<br>math.ceil<br>math.cos<br>math.deg<br>math.exp<br>math.floor<br></ul>|<ul>math.fmod<br>math.frexp<br>math.huge<br>math.ldexp<br>math.log<br>math.log10<br>math.max<br>math.min<br>math.modf<br>math.pi<br></ul>|<ul>math.pow<br>math.rad<br>math.random<br>math.randomseed<br>math.sin<br>math.sinh<br>math.sqrt<br>math.tan<br>math.tanh<br><br></ul>





### FOOTNOTES
| <!-- -->    | <!-- -->    |
|-------------|-------------|
|  **[FN1]**  | The numbers on the left substitute for the mouse buttons on the right, when used as arguments for functions (e.g., `PressMouseButton(`~~\"MButton\"~~ 2`)`).         |
|  **[FN2]**  | LButton (1) not reported by default. Use `EnablePrimaryMouseButtonEvents(true)` to override.<p>|
