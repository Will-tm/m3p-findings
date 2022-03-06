# M3P FINDINGS

## Purpose

In this file I'll collect things that I've found about the drone, useful parameters and other stuff that might help other people. 
Pay close attention to [Drone Hacks](https://drone-hacks.com/) and [No Limit Dronez](https://nolimitdronez.com/) for advanced stuff.

## Tools

* [OG's DJI Firmware Tools](https://github.com/o-gs/dji-firmware-tools/)
* Any linux distribution
* Shell files

## AC

### Parameters

To dump all parama, issue the following command:
`./comm_og_service_tool.py --bulk MAV3 FlycParam list --count 1500 --fmt=csv`

#### Disable leds

You can disable the christmas LED lights on the arms with the parameter `forearm_led_ctrl|g_config.misc_cfg.forearm_lamp_ctrl`. It's a bitmask. Right most digit controls the front leds, 3rd digit from the right the back leds. Which means:

* 5 = Both LEDs on
* 4 = Only back LEDs on
* 1 = Only front LEDs on
* 0 = All LEDs off

`./comm_og_service_tool.py --bulk MAV3 FlycParam set "forearm_led_ctrl|g_config.misc_cfg.forearm_lamp_ctrl" --alt 0xfe`

Parameter name has a pipe on it so you need to issue it withe `--alt` flag.

#### Sports mode boost

`./comm_og_service_tool.py --bulk MAV3 FlycParam set "mode_sport_cfg_vert_vel_down|g_config.mode_sport_cfg.vert_vel_down" --alt -8`
`./comm_og_service_tool.py --bulk MAV3 FlycParam set "mode_sport_cfg_vert_vel_up|g_config.mode_sport_cfg.vert_vel_up" --alt 10`

