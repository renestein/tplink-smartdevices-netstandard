# TPLinkSmartBulb Class
<small>Namespace: TPLinkSmartDevices.Devices</small><br/>
<small>Inheritance: TPLinkSmartDevice -> TPLinkSmartBulb</small><br/><br/>
encloses bulb specific system information and bulb controls

## Properties

### `IsColor`
: Returns whether bulb supports color changes
``` csharp
public bool IsColor { get; private set; }
```

### `IsDimmable`
: Returns whether bulb supports dimming the brightness
``` csharp
public bool IsDimmable { get; private set; }
```

### `IsVariableColorTemperature`
: Returns whether bulb supports changing of color temperature
``` csharp
public bool IsVariableColorTemperature { get; private set; }
```

### `Brightness`
: Returns bulb brightness in percent
``` csharp
public int Brightness { get; private set; }
```

### `ColorTemperature`
: Returns bulbs color temperature in kelvin
``` csharp
public int ColorTemperature { get; private set; }
```

### `HSV`
: Returns bulb color in HSV scheme 
``` csharp
public BulbHSV HSV { get; private set; }
```

### `PoweredOn`
: Returns whether bulb is powered on 
``` csharp
public bool PoweredOn { get; private set; }
```

## Constructors

### `TPLinkSmartBulb(string, int)`
: Creates a new object of this type, used for KL100/KL110/KL130 bulbs 
  ``` csharp
  public TPLinkSmartBulb(string hostname, int port=9999)
  ```

    __Parameters__
    : * `#!csharp string hostname`: ip-address of of this bulb
      * `#!csharp int port`: bulb communicates on this port, defaults to `9999`

## Methods

### `Refresh()`
: Refreshes all properties of this bulb (includes a call to [`TPLinkSmartDevice.Refresh(dynamic)`](device.md#refreshdynamic) for the common device information)
  ``` csharp
  public async Task Refresh()
  ```

!!! tip "Method is awaitable" 

### `SetPoweredOn(bool)`
: Change the power state of this bulb 
  ``` csharp
  public void SetPoweredOn(bool value)
  ```

    __Parameters__
    : * `#!csharp bool value`: `true` power on, `false` power off

### `SetBrightness(int)`
: Change the bulbs brightness
  ``` csharp
  public void SetBrightness(int brightness)
  ```

    __Parameters__
    : * `#!csharp int brightness`: brightness value in percent

    __Exceptions__
    : * `#!csharp NotSupportedException`: the bulb does not support dimming

### `SetColorTemp(int)`
: Change the bulbs color temperature
  ``` csharp
  public void SetColorTemp(int colortemp)
  ```

    __Parameters__
    : * `#!csharp int colortemp`: color temperature in kelvin, common values ranging between 2700K (soft light) to 6500K (bright daylight)

    __Exceptions__
    : * `#!csharp NotSupportedException`: the bulb does not support color temperature changes

!!! note 
    Color temperature values depend on device model, for instance KL120 supports 2500K-5000K and KL130 2700K-9000K!

### `SetColorTemp(BulbHSV)`
: Change the bulbs color 
  ``` csharp
  public void SetHSV(BulbHSV hsv)
  ```

    __Parameters__
    : * `#!csharp BulbHSV hsv`: color in HSV color scheme, see [`BulbHSV`](/docs/data/hsv) reference

    __Exceptions__
    : * `#!csharp NotSupportedException`: the bulb does not support color changes
    