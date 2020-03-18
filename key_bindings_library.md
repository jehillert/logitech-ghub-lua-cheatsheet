## LUA-LOGITECH KEYBINDINGS AND SCRIPT COLLECTION

### THINGS TO NOTE
_[1] The scripts are basic because my Lua skills are basic.  I am posting them because I there seems to be a complete lack of basic bindings and scripts online.  Take'em or leave'em.  Either way, they get the job done._

_[2] I explain what each script does by providing the Autohotkey equivalent. This is mostly because it is easier at the end of the end to explain it this way then to write clear english.  If clarification is desired on some point, please feel free to ask._

_[3] '███' and 'doSomething()' are placeholders for user input.  For the former, substitute in any arguments that the Logitech API function will except. For the latter, execute any valid output functionality_

_[4] If you do not see an OnEvent() statement in a block of code, it was left out for convenience.  Assume the code needs to be wrapped by OnEvent() to run.  In other words, everything below follows the following formula:_
```lua
function OnEvent(event, arg)
-- A block of code from below
end
```

_[5] These scripts were only validated for a Logitech G903 Light Speed mouse. They may not work on other devices._

### BINDINGS & SCRIPTS
__RButton && LButton::SendInput ^{LButton}__
```lua
function OnEvent(event, arg)
  if (event == "MOUSE_BUTTON_PRESSED" and arg == 2) then
    rbutton_down=true
  end

  if (event == "MOUSE_BUTTON_RELEASED" and arg == 2) then
    rbutton_down=false
  end

  if (event == "MOUSE_BUTTON_PRESSED" and arg == 1 and rbutton_down == true) then
      PressKey("lctrl")
      PressAndReleaseMouseButton(1)
      ReleaseKey("lctrl")
  end
end
```

__RButton && WheelRight::SendInput ^{LButton}__
```lua
function OnEvent(event, arg)
  if (event == "MOUSE_BUTTON_PRESSED" and arg == 2) then
    rbutton_down=true
  end

  if (event == "MOUSE_BUTTON_RELEASED" and arg == 2) then
    rbutton_down=false
  end

  if (event == "MOUSE_BUTTON_PRESSED" and arg == 1 and rbutton_down == true) then
      if (rbutton_down == true ) then
        PressKey("lctrl")
      end
      PressAndReleaseMouseButton(1)
      if (rbutton_down == true ) then
        ReleaseKey("lctrl")
      end
  end
end
```
```lua```
```lua```
```lua```
```lua```
```lua```
```lua```
```lua```
```lua```
```lua```

(RIGHT CLICK + LEFT CLICK ==> DO SOMETHING)
```lua
function OnEvent(event, arg)
  if (event == "MOUSE_BUTTON_PRESSED" and arg == 2) then
    rbutton_down=true
  end

  if (event == "MOUSE_BUTTON_RELEASED" and arg == 2) then
    rbutton_down=false
  end

  if (event == "MOUSE_BUTTON_PRESSED" and arg == 1 and rbutton_down == true) then
    doSomething()
  end
end
```
