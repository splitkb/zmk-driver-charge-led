# Splitkb.com ZMK charge LED driver

This driver adds support for a charging LED. 

## Battery empty LED

Blinks the specified LED 20 times in short bursts when the battery percentage is 20% or lower.

Devicetree example:
```
/ {
    battery_empty_led: battery_empty_led {
        compatible = "splitkb,battery-empty-led";
        status = "okay";
        led = <&orange_led>; 
    };
};
```

## Charging IC LED

Sets the specified LED to `ON` when a charger is connected. This is done by reading the STAT pin from a BQ25170 charging IC.

Devicetree example:
```
/ {
    charging_led_controller {
        compatible = "splitkb,charging-ic-led";
        status = "okay";
        stat-gpios = <&gpio1 6 (GPIO_ACTIVE_LOW | GPIO_PULL_UP)>;
        led = <&orange_led>; 
    };
};
```
