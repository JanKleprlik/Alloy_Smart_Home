# Alloy homework

# assignment
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

# documentaion

I have decided to do the smart home version in alloy. The solution is heavily inspired by "smart home" from google. Devices ihnerit from abstract base `Device` and each device contains given set of traits. Those devices are then assigned to rooms. Everything is identified by an unique ID.

