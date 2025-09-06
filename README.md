# Home Assistant HVAC Algorithm

An intelligent thermostat automation script for Home Assistant that controls a Nest Learning Thermostat based on occupancy, weather conditions, and time-based schedules.

## Functionality

The script automatically adjusts HVAC settings based on multiple conditions:

- **Occupancy Control**: Turns off HVAC when family is away
- **Weather-Based Logic**: Uses outside temperature to determine heating vs cooling strategies
- **Schedule Awareness**: Different temperature settings for work hours and time-based nighttime schedules
- **Energy Optimization**: Turns off cooling when outside temperature is lower than inside
- **Smart Notifications**: Sends SMS alerts when natural cooling opportunities are available
- **Forecast Integration**: Disables heating when daily forecast predicts warm weather

## Configuration Variables

| Variable                       |  Default | Description                                                           |
|--------------------------------|---------:|-----------------------------------------------------------------------|
| `threshold_temp`               |     10°C | Temperature threshold for switching between heating and cooling modes |
| `cooling_work_temp`            |     25°C | Cooling temperature during work hours                                 |
| `heating_work_temp`            |     16°C | Heating temperature during work hours (when away)                     |
| `cooling_night_temp`           |     21°C | Cooling temperature during nighttime                                  |
| `heating_night_temp`           |     16°C | Heating temperature during nighttime                                  |
| `cooling_default_temp`         |   23.5°C | Default cooling temperature                                           |
| `heating_default_temp`         |   21.5°C | Default heating temperature                                           |
| `forecast_threshold_low_temp`  |      5°C | Forecast low temperature threshold for disabling heating              |
| `forecast_threshold_high_temp` |     15°C | Forecast high temperature threshold for disabling heating             |
| `cooling_nighttime`            | 19:00:00 | Time when cooling nighttime schedule begins                           |
| `heating_nighttime`            | 22:00:00 | Time when heating nighttime schedule begins                           |
| `cooling_daytime`              | 08:00:00 | Time when cooling daytime schedule begins                             |
| `heating_daytime`              | 07:00:00 | Time when heating daytime schedule begins                             |

## Dependencies

### Required Entities
- `climate.nest_learning_thermostat` - Main thermostat control
- `binary_sensor.family_status` - Home/away occupancy detection
- `weather.winnipeg` - Weather data source
- `sensor.winnipeg_temperature` - Current outdoor temperature
- `sensor.nest_learning_thermostat_temperature` - Indoor temperature
- `binary_sensor.worktime_sensor` - Work hours detection
- `device_tracker.seuns_iphone` - Individual presence tracking
- `sensor.winnipeg_low_today` - Daily low temperature forecast
- `sensor.winnipeg_high_today` - Daily high temperature forecast

### Services
- `notify.mobile_app_vadimiphone` - SMS notification service for cooling alerts

## Installation

1. Place the script in your Home Assistant scripts configuration
2. Ensure all required entities are properly configured
3. Customize temperature variables as needed for your preferences
4. Test the automation with different scenarios to verify proper operation 
