# Alloy homework

## Assignment
topic: models in VDM or Alloy

task 1: create model for "smart home" or "automated smart warehouse"
  !! pick just one option !!

  option A: smart home
      - important aspects: various sensors, control, security and other equipment
      - you have to decide what entities and operations to capture in the model
          - example: temperature (heating), smoke, lights, cameras, movement, automated locking
          - example: automatically turn on/off some devices based on values recorded by sensors
      - do not forget to define some assertions (facts) and commands (run, check)

  option B: automated smart warehouse
      - context: modern partially automated warehouses equipped with many robots
      - what to capture in your model: packages (items), robots (transporting packages around the warehouse), human employees (their specific roles and interaction with robots), warehouse environment (tracks and virtual "roads" for the robots, various necessary equipment, other important "hardware", etc)
      - define some important properties of the dynamic/runtime state of the warehouse (some invariants, guarantees)

task 2: document your solution
	- explain key design decisions and more advanced usage of VDM/Alloy

note: you can define the model in VDM or Alloy (pick one language)

deadline: 31.12.2022

resources about "smart home" (list of possible functionality)
	https://www.alza.cz/smarthome-inteligentni-domacnost/18855843.htm
	https://developers.home.google.com/cloud-to-cloud
	https://developers.google.com/assistant/smarthome/overview

resources for "automated smart warehouse" (some in Czech)
	https://www.idnes.cz/ekonomika/domaci/rohlik-roboty-sklad-e-commerce.A221110_101029_ekonomika_vebe
	https://www.idnes.cz/ekonomika/podniky/zasilkovna-roboti-vanoce-zamestnanci-hospodareni.A221011_123048_ekoakcie_vebe
	https://www.autostoresystem.com/
	https://www.netsuite.com/portal/resource/articles/inventory-management/warehouse-automation.shtml
	https://www.selecthub.com/warehouse-management/building-automated-warehouse-system/

## Documentaion

I have decided to do the smart home version in alloy. The solution is inspired by "smart home" from google. It must be said that this model of smart home is very simple and some details were ommited for brevity as compared to the google inspiration.

There is one `Home` which consists of `Room`s. Devices ihnerit from an abstract base `Device` and are further divided into indoor and outdoor devices for simpler definition of concrete devices such as `Lawnmover` or `Lock` . Concrete devices contains specific set of traits such as `roomsToClean` for a `Vacuum`. Indoor devices are assigned room and outdoor devices are assigned to a home.

Each device must have a sensor to trigger its functioanlity. Such sensor can be a `ManualDetector` which represents remote control which accepts input from user for example. I have decided not to use single hub, which would mediate inputs from sensors to devices but rather a complex network of individual devices which communicate directly with corresponding sensors. I find such hub as unnecessary bottleneck.

Chcecks and predicates are inspired by lecture and [alloy tutorial](http://alloytools.org/tutorials/online/frame-FS-6.html) where original and new states are used. I used suffix *N* to represent new states.
