Linux font-config 配置
======================

## 中文配置示例

`nvim ~/.config/fontconfig/fonts.conf`
```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <!-- Default system-ui fonts -->
  <match target="pattern">
    <test name="family">
      <string>system-ui</string>
    </test>
    <edit name="family" mode="prepend" binding="strong">
      <string>sans-serif</string>
    </edit>
  </match>

  <!-- Default sans-serif fonts-->
  <match target="pattern">
    <test name="family">
      <string>sans-serif</string>
    </test>
    <edit name="family" mode="prepend" binding="strong">
      <string>Noto Sans CJK SC</string>
      <string>Noto Sans</string>
      <string>Twemoji</string>
    </edit>
  </match>

  <!-- Default serif fonts-->
  <match target="pattern">
    <test name="family">
      <string>serif</string>
    </test>
    <edit name="family" mode="prepend" binding="strong">
      <string>Noto Serif CJK SC</string>
      <string>Noto Serif</string>
      <string>Twemoji</string>
    </edit>
  </match>

  <!-- Default monospace fonts-->
  <match target="pattern">
    <test name="family">
      <string>monospace</string>
    </test>
    <edit name="family" mode="prepend" binding="strong">
      <string>Noto Sans Mono CJK SC</string>
      <string>Symbols Nerd Font</string>
      <string>Twemoji</string>
    </edit>
  </match>
  <match target="pattern">
    <test name="family" compare="contains">
      <string>Source Code</string>
    </test>
    <edit name="family" binding="strong">
      <string>Fira Code</string>
    </edit>
  </match>
</fontconfig>
```