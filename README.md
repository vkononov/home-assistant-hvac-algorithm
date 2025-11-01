# Home Assistant HVAC Algorithm

An intelligent thermostat automation script for Home Assistant that controls a Nest Learning Thermostat based on occupancy, weather conditions, and time-based schedules.

## Functionality

The script automatically adjusts HVAC settings based on multiple conditions:

- **Occupancy Control**: Turns off HVAC when family is away
- **Weather-Based Logic**: Uses outside temperature to determine heating vs cooling strategies
- **Schedule Awareness**: Different temperature settings for work hours, daytime, evening, and nighttime schedules
- **Energy Optimization**: Turns off cooling when outside temperature is lower than inside temperature
- **Smart Notifications**: Sends SMS alerts when natural cooling opportunities are available (outside cooler than inside)
- **Forecast Integration**: Disables heating when daily forecast predicts warm weather
- **Presence Detection**: Adjusts heating during work hours based on individual presence

## Configuration Variables

| Variable                          |  Default | Description                                                           |
|-----------------------------------|---------:|-----------------------------------------------------------------------|
| `cooling_day_start_time`          | 08:00:00 | Time when cooling daytime schedule begins                             |
| `cooling_day_setpoint_c`          |   23.5°C | Default cooling temperature during daytime                            |
| `cooling_night_setpoint_c`        |     21°C | Cooling temperature during nighttime                                  |
| `cooling_night_start_time`        | 19:00:00 | Time when cooling nighttime schedule begins                           |
| `cooling_work_setpoint_c`         |     25°C | Cooling temperature during work hours                                 |
| `heating_day_start_time`          | 07:00:00 | Time when heating daytime schedule begins                             |
| `heating_day_setpoint_c`          |   21.5°C | Default heating temperature during daytime                            |
| `heating_evening_setpoint_c`      |     19°C | Heating temperature during evening hours                              |
| `heating_evening_start_time`      | 19:00:00 | Time when heating evening schedule begins                             |
| `heating_night_setpoint_c`        |     16°C | Heating temperature during late night                                 |
| `heating_night_start_time`        | 22:00:00 | Time when heating nighttime schedule begins                           |
| `heating_work_setpoint_c`         |     16°C | Heating temperature during work hours (when away)                     |
| `seasonal_mode_switch_temp_c`     |     10°C | Temperature threshold for switching between heating and cooling modes |
| `forecast_high_warm_threshold_c`  |     15°C | Forecast high temperature threshold for disabling heating             |
| `forecast_low_warm_threshold_c`   |      5°C | Forecast low temperature threshold for disabling heating              |

## Dependencies

### Required Entities
- `climate.nest_learning_thermostat` - Main thermostat control
- `binary_sensor.family_status` - Home/away occupancy detection
- `weather.winnipeg_forecast` - Weather data source
- `sensor.winnipeg_temperature` - Current outdoor temperature
- `sensor.nest_learning_thermostat_temperature` - Indoor temperature
- `binary_sensor.worktime_sensor` - Work hours detection
- `device_tracker.seunphone_unifi` - Individual presence tracking for Seun
- `sensor.winnipeg_low_temperature` - Daily low temperature forecast
- `sensor.winnipeg_high_temperature` - Daily high temperature forecast

### Services
- `notify.mobile_app_vadimiphone` - SMS notification service for cooling alerts

## Installation

1. Place the script in your Home Assistant scripts configuration
2. Ensure all required entities are properly configured
3. Customize temperature variables as needed for your preferences
4. Test the automation with different scenarios to verify proper operation 
