# Gluon-tutorial-projects

1. Accessing device information:
    For accessing device information we need to -
    - check if DeviceService is present.
    - Add 'device' module to downConfig in build.gradle file.
    
    ```
        downConfig {
            version = '3.7.0'
            plugins 'display', 'lifecycle', 'statusbar', 'storage', 'device'
        }
    ```
    - The build app must have to be run on any mobile device.
    
    The code is as follows:
    
    ```java
        Services.get(DeviceService.class).ifPresent(service2 -> {
            button.setOnAction(ex->{
                System.out.println("Device Model Name: "+ service2.getModel());
                MobileApplication.getInstance().showMessage("Device Model Name: "+ service2.getModel());
            });
        });
    ```
    
2. Accessing GPS:
    For accessing Position service, we need to -
    - check if PositionService is present.
    - Add 'position' module to downConfig in build.gradle file.
    
    ```
        downConfig {
            version = '3.7.0'
            plugins 'display', 'lifecycle', 'statusbar', 'storage', 'position'
        }
    ```
    - Add the latest dependency in the build.gradle dependencies section. Note that dependencies will have to be added below the               mainclassname, not inside the buildscript section.
    
    ```
        dependencies {
            compile 'com.gluonhq:charm:4.4.1'
        }
    ```
    - The device must have to have a GPS module.
    
    The code is as follows:
    
    ```java
        Services.get(PositionService.class).ifPresent(service -> {
            service.positionProperty().addListener((obs, ov, nv) ->
            // enable button and add listener to retrieve coordinates
            button.setOnAction(e -> {
                Position position = service.getPosition();
                MobileApplication.getInstance().showMessage("Latest known GPS coordinates from device:\n" +
                        position.getLatitude() + ", " + position.getLongitude());

            });
        });
    ```
