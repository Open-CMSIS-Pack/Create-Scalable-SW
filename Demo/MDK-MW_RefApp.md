# MDK-Middleware Reference Applications Demo

## Scope of the Demo
- [Reference Applications](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md)
  - [Overview](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#overview)
  - [Middleware Reference Applications](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#middleware-reference-applications)
    - [MDK-Middleware Reference Applications](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#mdk-middleware-reference-applications)
- [Usage](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#usage)
  - [Refer to layers](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#refer-layers-in-cmsis_pack_root)
  - [Copy layers](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#copy-layers-to-csolution-project)
- Targets used in Demo:
  - [STMicroelectronics B-U585I-IOT02A Discovery kit for IoT node with STM32U5 series](https://www.st.com/en/evaluation-tools/b-u585i-iot02a.html)
  - [NXP i.MX RT1050 Evaluation Kit](https://www.nxp.com/design/design-center/development-boards-and-designs/i-mx-evaluation-and-development-boards/i-mx-rt1050-evaluation-kit:MIMXRT1050-EVK)

## Demo Prerequisites
- Visual Studio Code with [Arm Keil Studio Pack extensions](https://marketplace.visualstudio.com/items?itemName=Arm.keil-studio-pack)
- [Tools avaialble via vcpkg](https://www.keil.arm.com/artifacts/)
  - [CMSIS-Toolbox](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/releases/)
  - Arm Compiler for Embedded
  - GCC compiler for ARM CPUs
- [CMSIS-Toolbox 2.5.0-devint1](https://github.com/brondani/cmsis-toolbox/releases/tag/2.5.0-devint1) (when using STM32CubeMX)
- [CMSIS Packs - public pack index](https://www.keil.arm.com/packs/)
  - [CMSIS 6.1.0](https://www.keil.arm.com/packs/cmsis-arm/versions/)
  - [CMSIS-Compiler 2.1.0](https://www.keil.arm.com/packs/cmsis-compiler-arm/versions/)
  - [CMSIS-RTX 5.9.0](https://www.keil.arm.com/packs/cmsis-rtx-arm/versions/)
  - Target: NXP EVKB-IMXRT1050 Board (Mounted Device: MIMXRT1052DVL6B)
    - [EVKB-IMXRT1050_BSP 18.0.0](https://www.keil.arm.com/packs/evkb-imxrt1050_bsp-nxp/versions/)
    - [MIMXRT1052_DFP 18.0.0](https://www.keil.arm.com/packs/mimxrt1052_dfp-nxp/devices/)
- CMSIS Packs - public repos [mapped as software pack](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/build-tools.md#install-a-repository)
  - [MDK-Middleware 8.0.0-dev](https://github.com/ARM-software/MDK-Middleware)  
    Install pack: `cpackget add <local_path>/Keil.MDK-Middleware.pdsc`
  - Target: STMicroelectronics B-U585I-IOT02A Board (Mounted Device: STM32U585AIIx)
    - [B-U585I-IOT02A_BSP 2.0.0-dev](https://github.com/Open-CMSIS-Pack/ST_B-U585I-IOT02A_BSP)  
      Install pack: `cpackget add <local_path>/Keil.B-U585I-IOT02A_BSP.pdsc`
    - [STM32U5xx_DFP 3.0.0-dev](https://github.com/Open-CMSIS-Pack/STM32U5xx_DFP)  
      Install pack: `cpackget add <local_path>/Keil.STM32U5xx_DFP.pdsc`
    - [CMSIS-Driver_STM32 1.0.0-dev0](https://github.com/Open-CMSIS-Pack/CMSIS-Driver_STM32)  
      Install pack: `cpackget add <local_path>/ARM.CMSIS-Driver_STM32.pdsc`
  - Target: NXP EVKB-IMXRT1050 Board (Mounted Device: MIMXRT1052DVL6B)
    - [IMXRT1050-EVKB_BSP 2.0.0-dev](https://github.com/Open-CMSIS-Pack/NXP_IMXRT1050-EVKB_BSP)  
      Install pack: `cpackget add <local_path>/Keil.IMXRT1050-EVKB_BSP.pdsc`
    - [CMSIS-Driver 2.9.0-dev](https://github.com/ARM-software/CMSIS-Driver)  
      Install pack: `cpackget add <local_path>/ARM.CMSIS-Driver.pdsc`
- CMSIS Packs - packs build from public repos and installed localy
  - Target: NXP EVKB-IMXRT1050 Board (Mounted Device: MIMXRT1052DVL6B)
    - [iMXRT105x_MWP 2.0.0-dev](https://github.com/Open-CMSIS-Pack/NXP_iMXRT105x_MWP)  
      Build pack: `gen_pack.sh`  
      Install pack: `cpackget add <local_path>/Keil.iMXRT105x_MWP.2.0.0-dev<n>.pack`

## Demo: MDK-Middleware Reference Application - USB Device

[MDK-Middleware](https://github.com/ARM-software/MDK-Middleware/tree/main/Documentation#readme) software pack contains components for IPv4 and IPv6 networking, USB Host and Device communication, as well as file system for data storage. 

[MDK-Middleware Examples](https://github.com/ARM-software/MDK-Middleware/tree/main/Examples) are reference applications that use defined interfaces (APIs) and are therefore hardware agnostic. These project examples show usage of middleware components and require a board layer with drivers for the specific target hardware.

[USB Device](https://github.com/ARM-software/MDK-Middleware/tree/main/Examples/USB/Device/)
- Open directory `USB Device` in Visual Studio Code (VS Code)
- Tools specified in `vcpkg-configuration.json` are automatically installed
  >Remove `cmsis-toolbox` from `vcpkg-configuration.json` to use the `2.5.0-devint1` version installed locally (when using STM32CubeMX)
- Use bash as command line interface
- Install local packs as described in [Demo Prerequisites](#demo-prerequisites)
- Target: STMicroelectronics B-U585I-IOT02A Board
  - Add target under `target-types:` to `USB_Device.csolution.yml`
    ```
        - type: B-U585I-IOT02A
          board: STMicroelectronics::B-U585I-IOT02A
    ```
  - Run `cbuild setup` to detect compatible board layers
    ```
    cbuild setup USB_Device.csolution.yml
    ```
  - Open `USB_Device.cbuild-idx.yml` and copy the `Board-Layer` variable to `USB_Device.csolution.yml`
    ```
          variables:
            - Board-Layer: <board_layer_path>.Board.clayer.yml
    ```
  - Copy layer to csolution project (use information from `USB_Device.cbuild-idx.yml`)
    ```
    mkdir -p <copy-to>
    cp -r <path> <copy-to>
    ```
  - Adjust `Board-Layer` variable in `USB_Device.csolution.yml` to reflect the copied layer path
  - Build the application: context `HID.Debug` (specify `--packs` to download missing packs)
    ```
    cbuild USB_Device.csolution.yml --context HID.Debug+B-U585I-IOT02A --update-rte --packs
    ```
  - [Optional]: Examine `*.cbuild.yml` which is the Software Bill-Of-Material (BOM) and lists build information, packs, components, licenses, ...
  - List generators
    ```
    csolution list generators USB_Device.csolution.yml
    ```
  - Run generator (CubeMX)
    ```
    csolution run -g CubeMX USB_Device.csolution.yml
    ```
  - Change configuration in STM32CubeMX
    - Tab `Pinout & Configuration`- Category `Security` - Component `AES`: enable `Activated`
    - Run `GENERATE CODE`
  - Updated `Board.cgen.yml` contains new files for AES (`stm32u5xx_hal_cryp.c` and `stm32u5xx_hal_cryp_ex.c`)
  - Build the modified application: context `HID.Debug`
      ```
    cbuild USB_Device.csolution.yml --context HID.Debug+B-U585I-IOT02A --update-rte
    ```
  - Use VS Code CMSIS extensions to build the application
    - Use `...` and `Clean Output Directories` (avoid conflict with previous CLI builds)
    - Use `Manage Solution Settings` - Project Name `HID` and Build Type `Debug`
    - Use `Build`
- Target: NXP EVKB-IMXRT1050 Board
  - Add target under `target-types:` to `USB_Device.csolution.yml`
    ```
        - type: EVKB-IMXRT1050
          board: NXP::EVKB-IMXRT1050
    ```
  - Run `cbuild setup` to detect compatible board layers
    ```
    cbuild setup USB_Device.csolution.yml
    ```
  - Open `USB_Device.cbuild-idx.yml` and copy the `Board-Layer` variable to `USB_Device.csolution.yml`
    ```
          variables:
            - Board-Layer: <board_layer_path>.Board.clayer.yml
    ```
  - Build the application: context `HID.Debug` (specify `--packs` to download missing packs)
    ```
    cbuild USB_Device.csolution.yml --context HID.Debug+EVKB-IMXRT1050 --update-rte --packs
    ```
  - Build the application: context `HID.Debug` with GCC
    ```
    cbuild USB_Device.csolution.yml --context HID.Debug+EVKB-IMXRT1050 --update-rte --toolchain GCC --rebuild
    ```
    >Remove startup for AC6 `<layer_local_path>/RTE/Device/MIMXRT1052DVL6B/startup_MIMXRT1052.S` to bypass current DFP limitation
