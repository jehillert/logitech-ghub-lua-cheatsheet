## LUA-LOGITECH KEYBINDINGS AND SCRIPT COLLECTION

### NOTE
_[1] The scripts are basic because my Lua skills are basic.  I am posting them because I there seems to be a complete lack of basic bindings and scripts online._

_[2] These scripts were only validated for a Logitech G903 Light Speed mouse. They may not work on other devices._

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
