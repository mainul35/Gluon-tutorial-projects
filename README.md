# Gluon-tutorial-projects

1. Accessing device information:
    For accessing device information we need to -
    - check if DeviceService is present.
    - Add 'device' module to downConfig in build.gradle file.
    - The build app must have to be run on any mobile device.
    
    The code is as follows:
    
    ```
        Services.get(DeviceService.class).ifPresent(service2 -> {
            button.setOnAction(ex->{
                System.out.println("Device Model Name: "+ service2.getModel());
                MobileApplication.getInstance().showMessage("Device Model Name: "+ service2.getModel());
            });
        });
    ```
