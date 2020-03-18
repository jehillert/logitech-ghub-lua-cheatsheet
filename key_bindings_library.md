## LUA-LOGITECH KEYBINDINGS AND SCRIPT COLLECTION

### THINGS TO NOTE
_[1] The scripts are basic because my Lua skills are basic.  I am posting them because I there seems to be a complete lack of basic bindings and scripts online.  Take'em or leave'em.  Either way, they get the job done._

_[2] '███' and 'doSomething()' are placeholders for user input.  For the former, substitute in any arguments that the Logitech API function will except. For the latter, execute any valid output functionality_

_[3] These scripts were only validated for a Logitech G903 Light Speed mouse. They may not work on other devices._

### BINDINGS & SCRIPTS
**RIGHT_CLICK + SOME_KEY ==> SOME_ACTION**
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
