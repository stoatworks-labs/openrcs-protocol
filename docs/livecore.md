# LiveCore series — variable reference

Transport: **TCP 10500**, commands terminated `LF`, replies CRLF. See [framing](framing.md) and the [variable model](variable-model.md).

**1014 variables** across **88 groups**. Each variable has a 5-character mnemonic (a few are 1-character), an index shape (`Dims`), an integer range, and read/write access. Replies use the same mnemonic except where a **Reply** column is shown.

## Groups

- [PC_CONTROL](#pc-control) (16)
- [PC_UPDATER](#pc-updater) (5)
- [PC_BOARD_INFO](#pc-board-info) (4)
- [PC_VERSION](#pc-version) (4)
- [PC_TEMPERATURE](#pc-temperature) (4)
- [PC_COUNTERS](#pc-counters) (6)
- [INTERFACES](#interfaces) (8)
- [STILLS_LIBRARY](#stills-library) (16)
- [INPUT_SET](#input-set) (2)
- [AUTOCALIB](#autocalib) (3)
- [WEBSERVER](#webserver) (2)
- [EDID_LIB](#edid-lib) (5)
- [FRONTPANEL](#frontpanel) (4)
- [MONITORING_LAYOUT](#monitoring-layout) (13)
- [MONITORING_LAYOUT_MEMORIES](#monitoring-layout-memories) (16)
- [PRESET_MEMORIES](#preset-memories) (65)
- [MASTER_PRESET_MEMORIES](#master-preset-memories) (11)
- [EMERGENCY_MEMORY](#emergency-memory) (2)
- [STARTUP_MEMORY](#startup-memory) (2)
- [CONFIDENCE_MEMORIES](#confidence-memories) (10)
- [LABEL_STRINGS](#label-strings) (9)
- [SIMPLE_PRESETS](#simple-presets) (2)
- [SIMPLE_PRESETS_CONTROL](#simple-presets-control) (6)
- [TPP](#tpp) (8)
- [VERTIGE](#vertige) (1)
- [SPU](#spu) (11)
- [SPU_UNIT](#spu-unit) (10)
- [SYSTEM](#system) (23)
- [SIMULATOR](#simulator) (1)
- [CONTROL](#control) (22)
- [DEVICE_INFO](#device-info) (18)
- [DEVICE_FLAGS](#device-flags) (8)
- [VERSION](#version) (5)
- [DOWNGRADE](#downgrade) (7)
- [INPUT](#input) (31)
- [INPUT_AUTOSET](#input-autoset) (2)
- [INPUT_AUTOCENTER](#input-autocenter) (2)
- [INPUT_AUTOCALIB](#input-autocalib) (3)
- [INPUT_SIGNALS](#input-signals) (35)
- [INPUT_SETTINGS](#input-settings) (49)
- [CREMATTE_ASSISTANT](#crematte-assistant) (8)
- [INPUT_SETTINGS_MEMORIES](#input-settings-memories) (64)
- [LARGE_STILLS](#large-stills) (23)
- [REDUCED_STILLS](#reduced-stills) (20)
- [STILLS_CAPTURE](#stills-capture) (10)
- [STILLS_CAPTURE_SLOT](#stills-capture-slot) (6)
- [SNAPSHOTS](#snapshots) (3)
- [NATIVE_SET](#native-set) (4)
- [PRESET_NATIVE](#preset-native) (9)
- [PRESET_ID](#preset-id) (3)
- [PRESET](#preset) (41)
- [PRESET_STATUS](#preset-status) (5)
- [MASTER_ALPHA](#master-alpha) (8)
- [STROBE](#strobe) (1)
- [GROUP_CONTROL](#group-control) (10)
- [SEQ_TAKE](#seq-take) (2)
- [GROUP_STUFF](#group-stuff) (1)
- [GROUP_STATUS](#group-status) (2)
- [LAYER_SWAP](#layer-swap) (5)
- [CONFIGURATION](#configuration) (4)
- [PERSPECTIVE](#perspective) (4)
- [SCREEN_MIRROR](#screen-mirror) (4)
- [SCREEN_LAYOUT](#screen-layout) (1)
- [CONFIDENTIAL](#confidential) (9)
- [OUTPUT](#output) (45)
- [OUTPUT_AOI_SIZE](#output-aoi-size) (7)
- [OUTPUT_AOI_STATUS](#output-aoi-status) (9)
- [OUTPUT_AUTOCALIB](#output-autocalib) (3)
- [FORMATS_COMPUTER_CUSTOM_COMPUTE](#formats-computer-custom-compute) (25)
- [FORMATS_COMPUTER_CUSTOM](#formats-computer-custom) (23)
- [OUTPUT_CONTROL](#output-control) (8)
- [SCREEN](#screen) (23)
- [OUTPUT_SCREEN](#output-screen) (17)
- [SOFTEDGE](#softedge) (8)
- [MONITORING__OUTPUTS](#monitoring--outputs) (43)
- [MONITORING_SCREEN](#monitoring-screen) (2)
- [MONITOING_OUTPUT_SCREEN](#monitoing-output-screen) (5)
- [MONITORING_AUTOCALIB](#monitoring-autocalib) (3)
- [FRAMELOCK_INPUT](#framelock-input) (8)
- [EDID_IN](#edid-in) (8)
- [EDID_OUT](#edid-out) (5)
- [EDID_MONITORING](#edid-monitoring) (5)
- [INTERNAL__FRAME__RATE](#internal--frame--rate) (10)
- [GPIO](#gpio) (10)
- [TALLY](#tally) (2)
- [TEMPERATURE](#temperature) (7)
- [FAN](#fan) (6)
- [COUPLING](#coupling) (34)


## PC_CONTROL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PCscf` | SAVE_CONFIGURATION | — | 0…1 | read/write |
| `PCrcf` | RESTORE_CONFIGURATION | — | 0…1 | read/write |
| `PCmrs` | POSMEMORYRESET | — | 0…1 | read/write |
| `PClor` | LOGOLIBRARY_RESET | — | 0…1 | read/write |
| `PCprs` | PEMEM_ALL_RESET | — | 0…1 | read/write |
| `PCmnr` | MON_MEM_ALL_RESET | — | 0…1 | read/write |
| `PCelr` | EDID_LIB_ALL_RESET | — | 0…1 | read/write |
| `PCocr` | OCFORMATS_ALL_RESET | — | 0…1 | read/write |
| `CTbri` | LCDBRIGHTNESS | — | 1…8 | read/write |
| `PCtbr` | THUMBNAIL_BIG_RESOLUTION | — | 0…1 | read/write |
| `PCdgs` | DEVICE_GLOBAL_STATE | — | 0…255 | read-only |
| `#` | DIESE | — | 0…3 | read/write |
| `/` | PORT_TYPE | — | 0…4 | read-only |
| `CTfar` | FACTORYRESET | — | 0…2 | read/write |
| `PCreb` | REBOOT_DEVICE | `[2]` | 0…1 | read/write |
| `PCsht` | SHUTDOWN_DEVICE | `[2]` | 0…2 | read/write |

## PC_UPDATER

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `UPver` | UPDATER_VERSION | `[2]` | 0…4294967295 | read-only |
| `UPsta` | UPDATER_START | `[2]` | 0…1 | read/write |
| `UPsto` | UPDATER_STOP | `[2]` | 0…1 | read/write |
| `UPprg` | UPDATER_PROGRESS | `[2]` | 0…100 | read/write |
| `UPsts` | UPDATER_STATUS | `[2]` | 0…3 | read/write |

## PC_BOARD_INFO

| Mnemonic | Reply | Name | Dims | Range | Access |
|---|---|---|---|---|---|
| `PCcrv` |  | PC_CARD_REV | `[2]` | 0…255 | read-only |
| `PCcst` |  | PC_CARD_STATUS | `[2]` | 0…65535 | read-only |
| `PCmac` | `Pcmac` | PC_MAC_ADDRESS | `[2,6]` | 0…255 | read-only |
| `PCopt` |  | PC_OPTION | `[2]` | 0…4294967295 | read-only |

## PC_VERSION

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PCver` | VER_PC | `[2]` | 0…65535 | read-only |
| `PCbld` | VER_BUILD | `[2]` | 0…4294967295 | read-only |
| `PCdom` | VER_DOM | `[2]` | 0…7 | read-only |
| `PCbio` | VER_BIOS | `[2]` | 0…255 | read-only |

## PC_TEMPERATURE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PCTcp` | PC_TEMP_CPU | `[2]` | 0…65535 | read-only |
| `PCTsy` | PC_TEMP_SYSTEM | `[2]` | 0…65535 | read-only |
| `PCTrf` | PC_TEMP_REFRESH | `[2]` | 0…1 | read/write |
| `PCTal` | PC_TEMP_ALARM | `[2]` | 0…2 | read-only |

## PC_COUNTERS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PCtmu` | PC_COUNTER_TIME_USE | `[2]` | 0…4294967295 | read-only |
| `PCtmt` | PC_COUNTER_TIME_TOTAL | `[2]` | 0…4294967295 | read-only |
| `PCtmr` | PC_COUNTER_REFRESH | `[2]` | 0…1 | read/write |
| `PCcyu` | PC_COUNTER_CYCLES_USE | `[2]` | 0…4294967295 | read-only |
| `PCcyr` | PC_COUNTER_CYCLES_USE_RESET | `[2]` | 0…1 | read/write |
| `PCcyt` | PC_COUNTER_CYCLES_USE_TOTAL | `[2]` | 0…4294967295 | read-only |

## INTERFACES

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `ITlip` | INTERFACE_LAN_IP | `[2,4]` | 0…255 | read/write |
| `ITlpo` | INTERFACE_LAN_PORT | `[2]` | 0…65535 | read/write |
| `ITlnk` | INTERFACE_LAN_NETMASK | `[2,4]` | 0…255 | read/write |
| `ITlgw` | INTERFACE_LAN_GATEWAY | `[2,4]` | 0…255 | read/write |
| `ITldp` | INTERFACE_DHCP | `[2]` | 0…1 | read/write |
| `ITudp` | INTERFACE_UPDATE | `[2]` | 0…1 | read/write |
| `ITres` | INTERFACE_RESET | `[2]` | 0…1 | read/write |
| `ITcct` | INTERFACE_CONNECTED_CONTROLLERS | `[2]` | 0…5 | read-only |

## STILLS_LIBRARY

| Mnemonic | Reply | Name | Dims | Range | Access |
|---|---|---|---|---|---|
| `SLusd` |  | STILL_USED | `[101]` | 0…1 | read/write |
| `SLred` | `Slred` | STILL_IS_REDUCED | `[101]` | 0…1 | read/write |
| `SLdhd` |  | STILL_IS_DUAL | `[101]` | 0…2 | read/write |
| `SLnbk` |  | STILL_IS_NATIVE | `[101]` | 0…1 | read/write |
| `Slval` |  | STILL_VALID | `[101]` | 0…3 | read-only |
| `SLiwd` |  | STILL_IMAGE_WIDTH | `[101]` | 0…4294967295 | read-only |
| `SLihe` |  | STILL_IMAGE_HEIGTH | `[101]` | 0…4294967295 | read-only |
| `SLclf` |  | STILL_CROP_LEFT | `[101]` | 0…65535 | read/write |
| `SLcrh` |  | STILL_CROP_RIGHT | `[101]` | 0…65535 | read/write |
| `SLcto` |  | STILL_CROP_TOP | `[101]` | 0…65535 | read/write |
| `SLcbo` |  | STILL_CROP_BOTTOM | `[101]` | 0…65535 | read/write |
| `SLcrp` |  | STILL_CROP_PREDEF | `[101]` | 0…4 | read/write |
| `SLain` |  | STILL_ASPECT_IN | `[101]` | 0…6 | read/write |
| `SLaou` |  | STILL_ASPECT_OUT | `[101]` | 0…3 | read/write |
| `SLiup` |  | STILL_IS_UPDATING | `[101]` | 0…2 | read-only |
| `SLera` |  | STILL_ERASE | `[101]` | 0…1 | read/write |

## INPUT_SET

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INasa` | IN_AUTOSET_ALL | — | 0…1 | read/write |
| `INasi` | IN_AUTOSET_INPUT | `[24]` | 0…1 | read/write |

## AUTOCALIB

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INaca` | IN_AUTOCALIBRATE_ALL | — | 0…1 | read/write |
| `INaci` | IN_AUTOCALIBRATE_INPUT | `[24]` | 0…1 | read/write |
| `OUaca` | OUT_AUTOCALIBRATE_ALL | — | 0…1 | read/write |

## WEBSERVER

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `WBpor` | WEBSERVER_PORT | `[2]` | 0…65535 | read-only |
| `WBcon` | WEBSERVER_CONNECTED_CONTROLLERS | `[2]` | 0…5 | read-only |

## EDID_LIB

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `Ediup` | EDID_LIB_IS_UPDATING | `[32]` | 0…1 | read-only |
| `EdLer` | EDID_LIB_ERASE | `[32]` | 0…1 | read/write |
| `Editr` | EDID_LIB_IS_TRANSFERING | — | 0…1 | read/write |
| `Edpsf` | EDID_LIB_IN_PLUG_SET_FACTORY | `[24,6]` | 0…1 | read/write |
| `EdIsf` | EDID_LIB_INPUTS_SET_FACTORY | — | 0…1 | read/write |

## FRONTPANEL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `FPena` | FRONTPANEL_ENABLE | `[2]` | 0…1 | read-only |
| `FPmti` | FRONTPANEL_UP_MENU_TIMEOUT | `[2]` | 0…255 | read-only |
| `FPmtx` | FRONTPANEL_MATRIX_KEYBOARD | `[2]` | 0…1 | read/write |
| `FPsht` | FRONTPANEL_SHUTDOWN_REQUEST | — | 0…1 | read/write |

## MONITORING_LAYOUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `MLupd` | MONITORING_UPDATE | `[2]` | 0…1 | read/write |
| `MLups` | MONITORING_UPDATE_STATUS | `[2]` | 0…1 | read/write |
| `MLres` | MONITORING_RESET | `[2]` | 0…1 | read/write |
| `MLfen` | MONITORING_FULLSCREEN_ENABLE | `[2]` | 0…1 | read/write |
| `MLfes` | MONITORING_FULLSCREEN_SOURCE | `[2]` | 0…55 | read/write |
| `MLfso` | MONITORING_FULLSCREEN_SHOW_OSD | `[2]` | 0…1 | read/write |
| `MLces` | MONITORING_CUSTOM_ELEMENT_SOURCE | `[2,12]` | 0…55 | read/write |
| `MLcso` | MONITORING_CUSTOM_ELEMENT_SHOW_OSD | `[2,12]` | 0…1 | read/write |
| `MLcen` | MONITORING_CUSTOM_ELEMENT_ENABLE | `[2,12]` | 0…1 | read/write |
| `MLcph` | MONITORING_CUSTOM_POSH | `[2,12]` | 0…65535 | read/write |
| `MLcpv` | MONITORING_CUSTOM_POSV | `[2,12]` | 0…65535 | read/write |
| `MLcsh` | MONITORING_CUSTOM_SIZEH | `[2,12]` | 0…65535 | read/write |
| `MLcsv` | MONITORING_CUSTOM_SIZEV | `[2,12]` | 0…65535 | read/write |

## MONITORING_LAYOUT_MEMORIES

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `MMsav` | MON_MEM_SAVE | `[2,8]` | 0…1 | read/write |
| `MMloa` | MON_MEM_LOAD | `[8,2]` | 0…1 | read/write |
| `MMres` | MON_MEM_RESET | `[8]` | 0…1 | read/write |
| `MMouw` | MON_MEM_OUTPUT_WIDTH | `[8]` | 0…65536 | read-only |
| `MMouh` | MON_MEM_OUTPUT_HEIGHT | `[8]` | 0…65536 | read-only |
| `MMmax` | MON_MEM_MAX_WIDGETS | `[8]` | 0…12 | read-only |
| `MMfen` | MON_MEM_FULLSCREEN_ENABLE | `[8]` | 0…1 | read/write |
| `MMfes` | MON_MEM_FULLSCREEN_SOURCE | `[8]` | 0…55 | read/write |
| `MMfso` | MON_MEM_FULLSCREEN_SHOW_OSD | `[8]` | 0…1 | read/write |
| `MMces` | MON_MEM_CUSTOM_ELEMENT_SOURCE | `[8,12]` | 0…55 | read/write |
| `MMcso` | MON_MEM_CUSTOM_ELEMENT_SHOW_OSD | `[8,12]` | 0…1 | read/write |
| `MMcen` | MON_MEM_CUSTOM_ELEMENT_ENABLE | `[8,12]` | 0…1 | read/write |
| `MMcph` | MON_MEM_CUSTOM_POSH | `[8,12]` | 0…65535 | read/write |
| `MMcpv` | MON_MEM_CUSTOM_POSV | `[8,12]` | 0…65535 | read/write |
| `MMcsh` | MON_MEM_CUSTOM_SIZEH | `[8,12]` | 0…65535 | read/write |
| `MMcsv` | MON_MEM_CUSTOM_SIZEV | `[8,12]` | 0…65535 | read/write |

## PRESET_MEMORIES

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PMscf` | PEMEM_SCREEN_FROM | — | 0…7 | read/write |
| `PMprf` | PEMEM_PRESET_FROM | — | 0…1 | read/write |
| `PMmet` | PEMEM_MEMORY_TO | — | 0…143 | read/write |
| `PMcat` | PEMEM_FILTER_CATEGORY | — | 0…4095 | read/write |
| `PMfim` | PEMEM_FILTER_SAVE_IN_MEMORY | — | 0…1 | read/write |
| `PMsav` | PEMEM_SAVE | — | 0…1 | read/write |
| `PMloa` | PEMEM_LOAD | — | 0…1 | read/write |
| `PMlot` | PEMEM_LOAD_AND_TAKE | — | 0…1 | read/write |
| `PMlse` | PEMEM_LOAD_SCALE_ENABLE | — | 0…1 | read/write |
| `PMres` | PEMEM_RESET | — | 0…1 | read/write |
| `PMscw` | PEMEM_SCREEN_WIDTH | `[144]` | 0…65536 | read-only |
| `PMsch` | PEMEM_SCREEN_HEIGHT | `[144]` | 0…65536 | read-only |
| `PMmly` | PEMEM_SCREEN_MAX_LAYERS | `[144]` | 0…24 | read-only |
| `PMsip` | PEMEM_IS_PERSPECTIVE | `[144]` | 0…1 | read-only |
| `PMmfc` | PEMEM_MEMORY_FILTER_CATEGORY | `[144]` | 0…4095 | read-only |
| `PMNin` | PEMEM_PN_INPUTSET | `[144]` | 0…8 | read/write |
| `PMNal` | PEMEM_PN_ALPHA | `[144]` | 0…256 | read/write |
| `PMNcr` | PEMEM_PN_COLOR_RED | `[144]` | 0…255 | read/write |
| `PMNcg` | PEMEM_PN_COLOR_GREEN | `[144]` | 0…255 | read/write |
| `PMNcb` | PEMEM_PN_COLOR_BLUE | `[144]` | 0…255 | read/write |
| `PMNot` | PEMEM_PN_CROSS_TRANSITION | `[144]` | 0…2 | read/write |
| `PMNow` | PEMEM_PN_CROSS_TRANSITION_WAY | `[144]` | 0…3 | read/write |
| `PMNos` | PEMEM_PN_CROSS_START_OFFSET | `[144]` | 0…65535 | read/write |
| `PMNoe` | PEMEM_PN_CROSS_END_OFFSET | `[144]` | 0…65535 | read/write |
| `PMinp` | PEMEM_INPUTNUM | `[144,24]` | 0…41 | read/write |
| `PMaov` | PEMEM_ASPECT_OVERRIDE | `[144,24]` | 0…4 | read/write |
| `PMflg` | PEMEM_FLAGS | `[144,24]` | 0…2147483647 | read/write |
| `PMmcv` | PEMEM_MASK_CURVE | `[144,24]` | 0…4294967295 | read/write |
| `PMalp` | PEMEM_ALPHA | `[144,24]` | 0…256 | read/write |
| `PMpoh` | PEMEM_POSH | `[144,24]` | 0…131072 | read/write |
| `PMpov` | PEMEM_POSV | `[144,24]` | 0…131072 | read/write |
| `PMpoz` | PEMEM_POSZ | `[144,24]` | 0…131072 | read/write |
| `PMsih` | PEMEM_SIZEH | `[144,24]` | 0…65535 | read/write |
| `PMsiv` | PEMEM_SIZEV | `[144,24]` | 0…65535 | read/write |
| `PMroh` | PEMEM_ROTH | `[144,24]` | 0…65535 | read/write |
| `PMrov` | PEMEM_ROTV | `[144,24]` | 0…65535 | read/write |
| `PMroz` | PEMEM_ROTZ | `[144,24]` | 0…65535 | read/write |
| `PMcph` | PEMEM_CROP_WIN_POS_H | `[144,24]` | 0…65535 | read/write |
| `PMcpv` | PEMEM_CROP_WIN_POS_V | `[144,24]` | 0…65535 | read/write |
| `PMcsh` | PEMEM_CROP_WIN_SIZE_H | `[144,24]` | 0…58981 | read/write |
| `PMcsv` | PEMEM_CROP_WIN_SIZE_V | `[144,24]` | 0…58981 | read/write |
| `PMbst` | PEMEM_BORDER_STYLE | `[144,24]` | 0…5 | read/write |
| `PMbcr` | PEMEM_BORDER_COLOR_RED | `[144,24]` | 0…255 | read/write |
| `PMbcg` | PEMEM_BORDER_COLOR_GREEN | `[144,24]` | 0…255 | read/write |
| `PMbcb` | PEMEM_BORDER_COLOR_BLUE | `[144,24]` | 0…255 | read/write |
| `PMbal` | PEMEM_BORDER_ALPHA | `[144,24]` | 0…255 | read/write |
| `PMbsh` | PEMEM_BORDER_SIZE_H | `[144,24]` | 0…127 | read/write |
| `PMbsv` | PEMEM_BORDER_SIZE_V | `[144,24]` | 0…127 | read/write |
| `PMotr` | PEMEM_OPENING_TRANSITION | `[144,24]` | 0…7 | read/write |
| `PMowa` | PEMEM_OPENING_TRANSITION_WAY | `[144,24]` | 0…10 | read/write |
| `PMctr` | PEMEM_CLOSING_TRANSITION | `[144,24]` | 0…7 | read/write |
| `PMcwa` | PEMEM_CLOSING_TRANSITION_WAY | `[144,24]` | 0…10 | read/write |
| `PMbah` | PEMEM_BEZIER_PT1_POSH | `[144,24]` | 0…65535 | read/write |
| `PMbav` | PEMEM_BEZIER_PT1_POSV | `[144,24]` | 0…65535 | read/write |
| `PMbaz` | PEMEM_BEZIER_PT1_POSZ | `[144,24]` | 0…65535 | read/write |
| `PMbbh` | PEMEM_BEZIER_PT2_POSH | `[144,24]` | 0…65535 | read/write |
| `PMbbv` | PEMEM_BEZIER_PT2_POSV | `[144,24]` | 0…65535 | read/write |
| `PMbbz` | PEMEM_BEZIER_PT2_POSZ | `[144,24]` | 0…65535 | read/write |
| `PMoso` | PEMEM_OPENING_START_OFFSET | `[144,24]` | 0…65535 | read/write |
| `PMoeo` | PEMEM_OPENING_END_OFFSET | `[144,24]` | 0…65535 | read/write |
| `PMcso` | PEMEM_CLOSING_START_OFFSET | `[144,24]` | 0…65535 | read/write |
| `PMceo` | PEMEM_CLOSING_END_OFFSET | `[144,24]` | 0…65535 | read/write |
| `PMtba` | PEMEM_TBAR_BEZIER_PT1 | `[144,24]` | 0…255 | read/write |
| `PMtbb` | PEMEM_TBAR_BEZIER_PT2 | `[144,24]` | 0…255 | read/write |
| `PMdur` | PEMEM_DURATION | `[144]` | 0…3000 | read/write |

## MASTER_PRESET_MEMORIES

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PSprf` | PESMEM_PRESET_FROM | — | 0…1 | read/write |
| `PSmet` | PESMEM_MEMORY_TO | — | 0…143 | read/write |
| `PSosm` | PESMEM_OP_SCREEN_MEMORY | `[8]` | 0…143 | read/write |
| `PSose` | PESMEM_OP_SCREEN_ENABLE | `[8]` | 0…1 | read/write |
| `PSsav` | PESMEM_SAVE | — | 0…2 | read/write |
| `PSloa` | PESMEM_LOAD | — | 0…1 | read/write |
| `PSlot` | PESMEM_LOAD_AND_TAKE | — | 0…1 | read/write |
| `PSres` | PESMEM_RESET | — | 0…1 | read/write |
| `PSval` | PESMEM_VALID | `[144]` | 0…1 | read-only |
| `PSssm` | PESMEM_SCREEN_MEMORY | `[144,8]` | 0…143 | read-only |
| `PSsse` | PESMEM_SCREEN_ENABLED | `[144,8]` | 0…2 | read-only |

## EMERGENCY_MEMORY

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `EGena` | EMG_MEMORY_ENABLE | `[4]` | 0…1 | read/write |
| `EGmet` | EMG_MEMORY_PESMEM_MEMORY | `[4]` | 0…143 | read/write |

## STARTUP_MEMORY

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SMena` | STARTUP_MEMORY_ENABLE | — | 0…1 | read/write |
| `SMmet` | STARTUP_MEMORY_PESMEM_MEMORY | — | 0…143 | read/write |

## CONFIDENCE_MEMORIES

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `CMsav` | CONFIDENCE_MEM_SAVE | `[8,16]` | 0…1 | read/write |
| `CMloa` | CONFIDENCE_MEM_LOAD | `[16,8]` | 0…1 | read/write |
| `CMres` | CONFIDENCE_MEM_RESET | `[16]` | 0…1 | read/write |
| `CMval` | CONFIDENCE_MEM_IS_VALID | `[16]` | 0…1 | read-only |
| `CMlab` | CONFIDENCE_MEM_LABEL | `[16,16]` | 0…126 | read/write |
| `CMlay` | CONFIDENCE_MEM_LAYOUT | `[16]` | 0…14 | read/write |
| `CMsca` | CONFIDENCE_MEM_SOURCE_1 | `[16]` | 0…56 | read/write |
| `CMscb` | CONFIDENCE_MEM_SOURCE_2 | `[16]` | 0…56 | read/write |
| `CMscc` | CONFIDENCE_MEM_SOURCE_3 | `[16]` | 0…56 | read/write |
| `CMscd` | CONFIDENCE_MEM_SOURCE_4 | `[16]` | 0…56 | read/write |

## LABEL_STRINGS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `LBInp` | INPUT_LABEL | `[24,6,16]` | 0…126 | read/write |
| `LBLgS` | LARGE_STILL_LABEL | `[8,16]` | 0…126 | read/write |
| `LBRdS` | REDUCED_STILL_LABEL | `[8,16]` | 0…126 | read/write |
| `LBOut` | OUTPUT_LABEL | `[8,16]` | 0…126 | read/write |
| `LBMon` | MONITORING_LABEL | `[2,16]` | 0…126 | read/write |
| `LBMMo` | MONITORING_MEM_LABEL | `[8,16]` | 0…126 | read/write |
| `LBScr` | SCREEN_LABEL | `[8,16]` | 0…126 | read/write |
| `LBPMe` | PEMEM_LABEL | `[144,16]` | 0…126 | read/write |
| `LBPSe` | PESMEM_LABEL | `[144,16]` | 0…126 | read/write |

## SIMPLE_PRESETS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SPPNi` | SP_PN_INPUTSET | `[8,2]` | 0…8 | read/write |
| `SPPEi` | SP_PE_INPUTNUM | `[8,2,24]` | 0…41 | read/write |

## SIMPLE_PRESETS_CONTROL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SPCtk` | SP_TAKE | `[8]` | 0…1 | read/write |
| `SPCtb` | SP_TBAR | `[8]` | 0…65535 | read/write |
| `SPscl` | SP_SCREEN_LIST | `[8]` | 0…1 | read/write |
| `SPtsl` | SP_TAKE_SCREEN_LIST | — | 0…1 | read/write |
| `SPslu` | SP_SET_SCREEN_LIST_ON_PESMEM_LOAD | — | 0…1 | read/write |
| `SPise` | SP_SCREEN_IS_ENABLED | `[8]` | 0…1 | read-only |

## TPP

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `TPdie` | DIESE_TPP | — | 0…3 | read/write |
| `TPver` | VER_TPP | `[2]` | 0…65535 | read-only |
| `TPbui` | BUILD_TPP | `[2]` | 0…4294967295 | read-only |
| `TPena` | TPP_ENABLE | `[2]` | 0…1 | read/write |
| `TPsts` | TPP_STATUS | `[2]` | 0…1 | read-only |
| `TPpor` | TPP_PORT | `[2]` | 0…65535 | read/write |
| `TPudp` | TPP_UPDATE | `[2]` | 0…1 | read/write |
| `TPcon` | TPP_CONNECTED_CONTROLLERS | `[2]` | 0…5 | read-only |

## VERTIGE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `VRcon` | VERTIGE_CONNECTED_CONTROLLERS | `[2]` | 0…3 | read-only |

## SPU

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SUava` | SPU_AVAILABLE | `[2]` | 0…1 | read-only |
| `SUpss` | SPU_POWER_SUPPLY_STATE | `[2]` | 0…3 | read-only |
| `SUaml` | SPU_ALARM_LEVEL | `[2]` | 0…2 | read-only |
| `SUupd` | SPU_UPDATE_VERSION | `[2]` | 0…4294967295 | read-only |
| `SUrev` | SPU_REV | `[2]` | 0…255 | read-only |
| `SUuid` | SPU_ID | `[2]` | 0…4294967295 | read-only |
| `SUcrc` | SPU_CRC | `[2]` | 0…65535 | read-only |
| `SUsrn` | SPU_SERIAL_NUM | `[2]` | 0…4294967295 | read-only |
| `SUsrr` | SPU_SERIAL_REF | `[2]` | 0…4294967295 | read-only |
| `SUdac` | SPU_DATECODE | `[2]` | 0…4294967295 | read-only |
| `SUdst` | SPU_DEVICE_STRING | `[2]` | 0…4294967295 | read-only |

## SPU_UNIT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SUuav` | SPU_UNIT_AVAILABLE | `[2,3]` | 0…1 | read-only |
| `SUgod` | SPU_UNIT_GOOD | `[2,3]` | 0…1 | read-only |
| `SUala` | SPU_UNIT_ALARM | `[2,3]` | 0…1 | read-only |
| `SUiav` | SPU_UNIT_INFOS_AVAILABLE | `[2,3]` | 0…1 | read-only |
| `SUman` | SPU_UNIT_INFO_MANUFACTURER | `[2,3]` | 0…3 | read-only |
| `SUivo` | SPU_UNIT_INFO_VOLTAGE | `[2,3]` | 0…65535 | read-only |
| `SUicu` | SPU_UNIT_INFO_CURRENT | `[2,3]` | 0…65535 | read-only |
| `SUitm` | SPU_UNIT_INFO_TEMPERATURE | `[2,3]` | 0…255 | read-only |
| `SUbat` | SPU_UNIT_BATTERY_CHARGE | `[2]` | 0…100 | read-only |
| `SUbch` | SPU_UNIT_BATTERY_IS_CHARGING | `[2]` | 0…1 | read-only |

## SYSTEM

| Mnemonic | Reply | Name | Dims | Range | Access |
|---|---|---|---|---|---|
| `!` | `PDEV` | DEV_PLATFORM | — | 97…97 | read-only |
| `?` | `DEV` | DEV | — | 0…119 | read-only |
| `SYdvl` |  | DEV_LIST | `[2]` | 0…119 | read-only |
| `SYvdb` |  | DBG_DEVICE | — | 0…1 | read/write |
| `Es` |  | DBG_CARD | — | 0…13 | read/write |
| `xX` |  | DBG_INDEX | `[6]` | 0…4294967295 | read/write |
| `@` | `ADBG` | DBG_ADDR | — | 0…4294967295 | read/write |
| `>` | `DDBG` | DBG_DATA | — | 0…4294967295 | read/write |
| `+` |  | DBG_SETBIT | — | 0…4294967295 | read/write |
| `-` |  | DBG_RESETBIT | — | 0…4294967295 | read/write |
| `SYdai` |  | DBG_DATA_IDX | `[2,14,65536]` | 0…4294967295 | read/write |
| `SYori` |  | DBG_OR_IDX | `[2,14,65536]` | 0…4294967295 | read/write |
| `SYani` |  | DBG_AND_IDX | `[2,14,65536]` | 0…4294967295 | read/write |
| `SYpub` |  | DBG_EN_PUBLIC | — | 0…1 | read/write |
| `SYpri` |  | DBG_EN_PRIVATE | `[2,14]` | 0…1 | read/write |
| `&` |  | ERROR | `[2,14]` | 0…4294967295 | read-only |
| `SYerl` |  | ERROR_LOG | `[2,14,4]` | 0…255 | read-only |
| `$` |  | DOLLAR | `[2,14]` | 0…4294967295 | read-only |
| `SYdie` |  | DIESE_EXT | — | 0…3 | read/write |
| `SYpcs` |  | PC_CARD_STARTED | — | 0…1 | read/write |
| `SYpig` |  | PING | — | 0…4294967295 | read/write |
| `*` |  | READY | — | 0…1 | read-only |
| `SYryl` |  | READY_LIST | `[2]` | 0…1 | read-only |

## SIMULATOR

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SIdev` | DEV_IS_SIMULATED | — | 0…1 | read-only |

## CONTROL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `CTfre` | FACTORYRESET_EXT | — | 0…2 | read/write |
| `CTsto` | CSTORE | — | 0…1 | read-only |
| `CTloc` | LOCK | — | 0…2 | read/write |
| `CTkbr` | KEYBRIGHTNESS | — | 10…100 | read/write |
| `CTaxi` | AXION | — | 0…1 | read/write |
| `CTaut` | AUTO_LOCK | — | 0…1 | read/write |
| `CTatk` | AUTO_TAKE | `[16]` | 0…1 | read/write |
| `CTpcm` | PRESET_COPY_MODE | `[16]` | 0…1 | read/write |
| `CTpmu` | PRESET_UPDATE_MODE | — | 0…1 | read/write |
| `CTpdm` | PRESET_DISPLAY_MODE | — | 0…1 | read/write |
| `CTpmd` | PREVIEW_MODE | — | 0…2 | read/write |
| `CTpcr` | PIP_COLOR_RED | — | 0…255 | read/write |
| `CTpcg` | PIP_COLOR_GREEN | — | 0…255 | read/write |
| `CTpcb` | PIP_COLOR_BLUE | — | 0…255 | read/write |
| `CTdcr` | DSK_COLOR_RED | — | 0…255 | read/write |
| `CTdcg` | DSK_COLOR_GREEN | — | 0…255 | read/write |
| `CTdcb` | DSK_COLOR_BLUE | — | 0…255 | read/write |
| `CTsbc` | SHADOW_BORDER_CORNER | — | 0…250 | read/write |
| `CTccr` | CONFIDENTIAL_COLOR_RED | — | 0…255 | read/write |
| `CTccg` | CONFIDENTIAL_COLOR_GREEN | — | 0…255 | read/write |
| `CTccb` | CONFIDENTIAL_COLOR_BLUE | — | 0…255 | read/write |
| `CTcmg` | CONFIDENTIAL_MARGIN | — | 0…80 | read/write |

## DEVICE_INFO

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `DIcid` | CARD_ID | `[2,20]` | 0…4294967295 | read-only |
| `DIcrv` | CARD_REV | `[2,20]` | 0…255 | read-only |
| `DIcip` | CARD_IS_PLUG | `[2,20]` | 0…1 | read-only |
| `DIcst` | CARD_STATUS | `[2,20]` | 0…1 | read-only |
| `DIcma` | CARD_MANDATORY | `[2,20]` | 0…1 | read-only |
| `DIcer` | CARD_ERROR | `[2,20]` | 0…1 | read-only |
| `DIcns` | CARD_NOT_STARTED | `[2,20]` | 0…1 | read-only |
| `DIohw` | OPTION_HW | `[2]` | 0…4294967295 | read-only |
| `DIosw` | OPTION_SW | `[2]` | 0…4294967295 | read-only |
| `DIcce` | CARD_CONFIG_ERROR | `[2]` | 0…1 | read-only |
| `DIcvs` | CARD_SERIAL_NUM | `[2,20]` | 0…4294967295 | read-only |
| `DIcvr` | CARD_REF | `[2,20]` | 0…4294967295 | read-only |
| `DIcvd` | CARD_DATECODE | `[2,20]` | 0…4294967295 | read-only |
| `DIdsn` | DEVICE_SERIAL_NUM | `[2]` | 0…4294967295 | read-only |
| `DIdre` | DEVICE_REF | `[2]` | 0…4294967295 | read-only |
| `DIddc` | DEVICE_DATECODE | `[2]` | 0…4294967295 | read-only |
| `DIdst` | DEVICE_STRING | `[2,4]` | 0…255 | read-only |
| `Dldlm` | DEVICE_LOW_MAINTENANCE | `[2]` | 0…1 | read-only |

## DEVICE_FLAGS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `DFltu` | FLAG_DEVICE_IS_3U | `[2]` | 0…1 | read-only |
| `DFlpr` | FLAG_LAYERS_PER_RESSOURCE | `[2]` | 0…255 | read-only |
| `DFseb` | FLAG_ESEB_AVAILABLE | `[2]` | 0…1 | read-only |
| `DFloe` | FLAG_DEVICE_IS_LOE | `[2]` | 0…1 | read-only |
| `DFspu` | FLAG_SPU_CONTROL_AVAILABLE | `[2]` | 0…1 | read-only |
| `DFplr` | FLAG_PERSPECTIVE_LAYER_AVAILABLE | `[2]` | 0…1 | read-only |
| `DFfrk` | FLAG_4K_AVAILABLE | `[2]` | 0…1 | read-only |
| `DFrpd` | FLAG_RESSOURCES_PER_DEVICE | `[2]` | 0…255 | read-only |

## VERSION

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `VEvar` | VER_VAR | `[2]` | 0…65535 | read-only |
| `VEupd` | VER_UPDATER | `[2]` | 0…4294967295 | read-only |
| `VEfga` | VER_FPGA | `[2,14,2]` | 0…4294967295 | read-only |
| `VEfts` | VER_FPGA_TIMESTAMP | `[2,14,2]` | 0…4294967295 | read-only |
| `VEmic` | VER_MICRO | `[2,14]` | 0…4294967295 | read-only |

## DOWNGRADE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `DGdev` | DOWNGRADE_DEV | — | 0…119 | read/write |
| `DGreq` | DOWNGRADE_REQUEST | — | 0…1 | read/write |
| `DGrst` | DOWNGRADE_RESET_REQUEST | — | 0…1 | read/write |
| `DGsuc` | DOWNGRADE_SUCCEED | — | 0…1 | read-only |
| `DGena` | DOWNGRADE_IS_ENABLE | — | 0…1 | read-only |
| `DGdlc` | DOWNGRADE_DEV_LIST_COMPATIBILITY | — | 0…4294967295 | read-only |
| `DGori` | DOWNGRADE_ORIG_DEV | — | 0…119 | read-only |

## INPUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INava` | IN_AVAILABLE | `[24]` | 0…1 | read-only |
| `INfrz` | IN_FREEZE | `[24]` | 0…1 | read/write |
| `INffz` | IN_FULL_FREEZE | `[24]` | 0…1 | read/write |
| `INbla` | IN_BLACK | `[24]` | 0…1 | read/write |
| `INpat` | IN_PATTERN | `[24]` | 0…5 | read/write |
| `INpcr` | IN_PATTERN_COLOR_RED | `[24]` | 0…255 | read/write |
| `INpcg` | IN_PATTERN_COLOR_GREEN | `[24]` | 0…255 | read/write |
| `INpcb` | IN_PATTERN_COLOR_BLUE | `[24]` | 0…255 | read/write |
| `INpid` | IN_PATTERN_ID_ENABLE | `[24]` | 0…1 | read/write |
| `INnat` | IN_IS_NATIVE | `[24]` | 0…1 | read/write |
| `INplg` | IN_PLUG | `[24]` | 0…5 | read/write |
| `INpav` | IN_PLUG_AVAILABLE | `[24,6]` | 0…1 | read-only |
| `INsrc` | IN_SOURCE | `[24,6]` | 0…512 | read/write |
| `INtya` | IN_TYPE_AVAILABLE | `[24,6,14]` | 0…1 | read-only |
| `INtyp` | IN_TYPE | `[24,6]` | 0…13 | read/write |
| `INdav` | IN_DUAL_LINK_AVAILABLE | `[24,6]` | 0…3 | read-only |
| `INdua` | IN_DUAL | `[24,6]` | 0…2 | read/write |
| `INdhc` | IN_DUAL_HEAD_CONFIG | `[24,6]` | 1…2 | read/write |
| `INdhi` | IN_DUAL_HEAD_LINKED_INPUT | `[24,6]` | 0…23 | read/write |
| `INdhp` | IN_DUAL_HEAD_LINKED_PLUG | `[24,6]` | 0…5 | read/write |
| `INsyl` | IN_SYNC_LOAD | `[24,6]` | 0…1 | read/write |
| `INstc` | IN_STETCH | `[24,6]` | 0…1 | read/write |
| `INuse` | IN_USED | `[24,6]` | 0…1 | read/write |
| `INsdd` | IN_SD_STD | `[24,6]` | 0…7 | read/write |
| `INsds` | IN_SD_STA | `[24,6]` | 0…1 | read/write |
| `INscf` | IN_SD_3D_COMB_FILTER | `[24,6]` | 0…3 | read/write |
| `INecf` | IN_ENABLE_CROP_FINDER | `[24,6]` | 0…1 | read/write |
| `INsyg` | IN_PLUG_SYNCHRO_GROUP | `[24,6]` | 0…4 | read/write |
| `INhdc` | IN_HDCP_ENABLE | `[24,6]` | 0…1 | read/write |
| `INish` | IN_SIZE_H | `[24]` | 0…65535 | read-only |
| `INisv` | IN_SIZE_V | `[24]` | 0…65535 | read-only |

## INPUT_AUTOSET

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INasp` | IN_AUTOSET_PLUG | `[24,6]` | 0…1 | read/write |
| `INapp` | IN_AUTOSET_PLUG_PROGRESS | `[24,6]` | 0…100 | read-only |

## INPUT_AUTOCENTER

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INain` | IN_AUTOCENTER_INPUT | `[24]` | 0…2 | read/write |
| `INaip` | IN_AUTOCENTER_INPUT_PROGRESS | `[24]` | 0…100 | read-only |

## INPUT_AUTOCALIB

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INcin` | IN_AUTOCALIB_INPUT | `[24]` | 0…1 | read/write |
| `INcsu` | IN_AUTOCALIB_PLUG_SUCCEED | `[24,6]` | 0…1 | read-only |
| `INcip` | IN_AUTOCALIB_PLUG_PROGRESS | `[24,6]` | 0…100 | read-only |

## INPUT_SIGNALS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `ISscc` | SIG_SCAN_COMPLETE | `[24,6]` | 0…1 | read-only |
| `ISspr` | SIG_SCAN_PRESENT | `[24,6]` | 0…1 | read-only |
| `ISsva` | SIG_SCAN_VALID | `[24,6]` | 0…1 | read-only |
| `ISdlw` | SIG_DUAL_LINK_WARNING | `[24,6]` | 0…1 | read-only |
| `ISuhw` | SIG_UH_FORMAT_WARNING | `[24,6]` | 0…1 | read-only |
| `ISdfo` | SIG_DETECTED_FORMAT | `[24,6]` | 0…62 | read-only |
| `IScfo` | SIG_CURRENT_FORMAT | `[24,6]` | 0…62 | read-only |
| `IScfn` | SIG_CURRENT_FORMAT_NAME | `[24,6,16]` | 0…255 | read-only |
| `ISlfo` | SIG_LIST_FORMAT | `[24,6,63]` | 0…1 | read-only |
| `ISswi` | SIG_SIGNAL_WIDTH | `[24,6]` | 0…65535 | read-only |
| `ISshe` | SIG_SIGNAL_HEIGHT | `[24,6]` | 0…65535 | read-only |
| `ISfwi` | SIG_FORMAT_WIDTH | `[24,6]` | 0…65535 | read-only |
| `ISfhe` | SIG_FORMAT_HEIGHT | `[24,6]` | 0…65535 | read-only |
| `ISiwi` | SIG_IMAGE_WIDTH | `[24,6]` | 0…65535 | read-only |
| `ISihe` | SIG_IMAGE_HEIGHT | `[24,6]` | 0…65535 | read-only |
| `ISfok` | SIG_FORMAT_KIND | `[24,6]` | 0…3 | read-only |
| `IShdc` | SIG_HDCP | `[24,6]` | 0…1 | read-only |
| `ISsnu` | SIG_SLOTNUMBER | `[24,6]` | 0…512 | read-only |
| `ISffi` | SIG_FREQ_FIELD | `[24,6]` | 0…4294967295 | read-only |
| `ISfli` | SIG_FREQ_LINE | `[24,6]` | 0…4294967295 | read-only |
| `IShpo` | SIG_HPOL | `[24,6]` | 0…1 | read-only |
| `ISvpo` | SIG_VPOL | `[24,6]` | 0…1 | read-only |
| `ISvss` | SIG_VSYNC_SIZE | `[24,6]` | 0…65535 | read-only |
| `IShss` | SIG_HSYNC_SIZE | `[24,6]` | 0…65535 | read-only |
| `ISsyt` | SIG_SYNC_TYPE | `[24,6]` | 0…3 | read-only |
| `ISsct` | SIG_SCANTYPE | `[24,6]` | 0…3 | read-only |
| `IShtt` | SIG_HTOTAL_THEORIC | `[24,6]` | 0…65535 | read-only |
| `IShtm` | SIG_HTOTALMAX | `[24,6]` | 0…65535 | read-only |
| `ISrcf` | SIG_REPEAT_COEFF | `[24,6]` | 1…10 | read-only |
| `IShvi` | SIG_HAS_AVI | `[24,6]` | 0…1 | read-only |
| `IScdh` | SIG_COLOR_DEPTH | `[24,6]` | 0…4 | read-only |
| `IScsp` | SIG_COLOR_SPACE | `[24,6]` | 0…10 | read-only |
| `ISidw` | SIG_IMAGE_DISPLAY_WIDTH | `[24,6]` | 0…65535 | read-only |
| `ISidh` | SIG_IMAGE_DISPLAY_HEIGHT | `[24,6]` | 0…65535 | read-only |
| `ISsty` | SIG_SDI_TYPE | `[24,6]` | 0…4 | read-only |

## INPUT_SETTINGS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `IEdef` | SET_DEFAULT | `[24,6]` | 0…1 | read/write |
| `IEufo` | SET_USER_FORMAT | `[24,6]` | 0…62 | read/write |
| `IEbhp` | SET_BLK_HPOS | `[24,6]` | 0…511 | read/write |
| `IEbvp` | SET_BLK_VPOS | `[24,6]` | 0…511 | read/write |
| `IEbhs` | SET_BLK_HSIZE | `[24,6]` | 0…511 | read/write |
| `IEbvs` | SET_BLK_VSIZE | `[24,6]` | 0…511 | read/write |
| `IEbri` | SET_BRIGHTNESS | `[24,6]` | 0…255 | read/write |
| `IEcon` | SET_CONTRAST | `[24,6]` | 0…255 | read/write |
| `IEclr` | SET_COLOR | `[24,6]` | 0…255 | read/write |
| `IEhue` | SET_HUE | `[24,6]` | 0…360 | read/write |
| `IEhto` | SET_HTOTAL_OFFSET | `[24,6]` | 0…511 | read/write |
| `IEpha` | SET_PHASE | `[24,6]` | 0…63 | read/write |
| `IEugr` | SET_USER_GAIN_R | `[24,6]` | 0…255 | read/write |
| `IEugg` | SET_USER_GAIN_G | `[24,6]` | 0…255 | read/write |
| `IEugb` | SET_USER_GAIN_B | `[24,6]` | 0…255 | read/write |
| `IEpdb` | SET_PULLDOWN_2_2 | `[24,6]` | 0…1 | read/write |
| `IEpdc` | SET_PULLDOWN_3_2 | `[24,6]` | 0…1 | read/write |
| `IEdll` | SET_DEINT_LOW_LATENCY | `[24,6]` | 0…1 | read/write |
| `IEudo` | SET_UNDEROVER | `[24,6]` | 0…1 | read/write |
| `IEain` | SET_ASPECT_IN | `[24,6]` | 0…6 | read/write |
| `IEaou` | SET_ASPECT_OUT | `[24,6]` | 0…3 | read/write |
| `IEpcr` | SET_CROP_PREDEF | `[24,6]` | 0…4 | read/write |
| `IEchs` | SET_CROP_LEFT | `[24,6]` | 0…4095 | read/write |
| `IEcvs` | SET_CROP_TOP | `[24,6]` | 0…4095 | read/write |
| `IEche` | SET_CROP_RIGHT | `[24,6]` | 0…4095 | read/write |
| `IEcve` | SET_CROP_BOTTOM | `[24,6]` | 0…4095 | read/write |
| `IEcmo` | SET_CRE_MODE | `[24,6]` | 0…4 | read/write |
| `IEcma` | SET_CRE_MASK | `[24,6]` | 0…2 | read/write |
| `IEcin` | SET_CRE_INVERT | `[24,6]` | 0…1 | read/write |
| `IEcrh` | SET_CRE_REF_H | `[24,6]` | 0…359 | read/write |
| `IEcrs` | SET_CRE_REF_S | `[24,6]` | 0…255 | read/write |
| `IEcrl` | SET_CRE_REF_L | `[24,6]` | 0…255 | read/write |
| `IEcoh` | SET_CRE_OFFSET_H | `[24,6]` | 0…255 | read/write |
| `IEcos` | SET_CRE_OFFSET_S | `[24,6]` | 0…255 | read/write |
| `IEcol` | SET_CRE_OFFSET_L | `[24,6]` | 0…255 | read/write |
| `IEcog` | SET_CRE_OFFSET_GLOBAL | `[24,6]` | 0…255 | read/write |
| `IEcch` | SET_CRE_COEF_H | `[24,6]` | 0…255 | read/write |
| `IEccs` | SET_CRE_COEF_S | `[24,6]` | 0…255 | read/write |
| `IEccL` | SET_CRE_COEF_L | `[24,6]` | 0…255 | read/write |
| `IEcah` | SET_CRE_ASPECT_H | `[24,6]` | 0…175 | read/write |
| `IEcas` | SET_CRE_ASPECT_S | `[24,6]` | 0…175 | read/write |
| `IEcde` | SET_CRE_DSK_ENABLE | `[24,6]` | 0…1 | read/write |
| `IEcda` | SET_CRE_DSK_ALPHA | `[24,6]` | 0…255 | read/write |
| `IEcrt` | SET_CREV_REF_TINT | `[24,6]` | 0…359 | read/write |
| `IEcaa` | SET_CREV_ALPHA_ANGLE | `[24,6]` | 1…180 | read/write |
| `IEcca` | SET_CREV_COLOR_ANGLE | `[24,6]` | 1…180 | read/write |
| `IEcga` | SET_CREV_GAIN | `[24,6]` | 0…4095 | read/write |
| `IEcof` | SET_CREV_OFFSET | `[24,6]` | 0…255 | read/write |
| `IEsha` | SET_SHARPNESS | `[24,6]` | 0…2 | read/write |

## CREMATTE_ASSISTANT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `CAimp` | CREMATTE_INPUT | — | 0…24 | read/write |
| `CAres` | CREMATTE_RESET | — | 0…1 | read/write |
| `CAgah` | CREMATTE_GRAB1_H | — | 0…65535 | read/write |
| `CAgav` | CREMATTE_GRAB1_V | — | 0…65535 | read/write |
| `CAgbh` | CREMATTE_GRAB2_H | — | 0…65535 | read/write |
| `CAgbv` | CREMATTE_GRAB2_V | — | 0…65535 | read/write |
| `CAgdi` | CREMATTE_GRAB_DISPLAY | — | 0…1 | read/write |
| `CAgad` | CREMATTE_GRAB_ADD | — | 0…1 | read/write |

## INPUT_SETTINGS_MEMORIES

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SMgin` | SETMEM_GLOBAL_INHIB | — | 0…1 | read/write |
| `SMids` | SETMEM_ID_SOURCE | `[513]` | 0…999 | read/write |
| `SMidt` | SETMEM_ID_TYPE | `[513]` | 0…13 | read/write |
| `SMidf` | SETMEM_ID_FREQ_FIELD | `[513]` | 0…4294967295 | read/write |
| `SMidl` | SETMEM_ID_FREQ_LINE | `[513]` | 0…4294967295 | read/write |
| `SMsyt` | SETMEM_ID_SYNC_TYPE | `[513]` | 0…3 | read/write |
| `SMidv` | SETMEM_ID_VSYNC_SIZE | `[513]` | 0…65535 | read/write |
| `SMidh` | SETMEM_ID_HSYNC_SIZE | `[513]` | 0…65535 | read/write |
| `SMida` | SETMEM_ID_VPOL | `[513]` | 0…1 | read/write |
| `SMidb` | SETMEM_ID_HPOL | `[513]` | 0…1 | read/write |
| `SMici` | SETMEM_ID_CREATOR_INPUT | `[513]` | 0…23 | read/write |
| `SMicp` | SETMEM_ID_CREATOR_PLUG | `[513]` | 0…5 | read/write |
| `SMufo` | SETMEM_USER_FORMAT | `[513]` | 0…62 | read/write |
| `SMhpo` | SETMEM_BLK_HPOS | `[513]` | 0…511 | read/write |
| `SMvpo` | SETMEM_BLK_VPOS | `[513]` | 0…511 | read/write |
| `SMhsi` | SETMEM_BLK_HSIZE | `[513]` | 0…511 | read/write |
| `SMvsi` | SETMEM_BLK_VSIZE | `[513]` | 0…511 | read/write |
| `SMbri` | SETMEM_BRIGHTNESS | `[513]` | 0…255 | read/write |
| `SMcon` | SETMEM_CONTRAST | `[513]` | 0…255 | read/write |
| `SMclr` | SETMEM_COLOR | `[513]` | 0…255 | read/write |
| `SMhue` | SETMEM_HUE | `[513]` | 0…360 | read/write |
| `SMhto` | SETMEM_HTOTAL_OFFSET | `[513]` | 0…511 | read/write |
| `SMpha` | SETMEM_PHASE | `[513]` | 0…63 | read/write |
| `SMugr` | SETMEM_USER_GAIN_R | `[513]` | 0…255 | read/write |
| `SMugg` | SETMEM_USER_GAIN_G | `[513]` | 0…255 | read/write |
| `SMugb` | SETMEM_USER_GAIN_B | `[513]` | 0…255 | read/write |
| `SMpdb` | SETMEM_PULLDOWN_2_2 | `[513]` | 0…1 | read/write |
| `SMpdc` | SETMEM_PULLDOWN_3_2 | `[513]` | 0…1 | read/write |
| `SMdll` | SETMEM_DEINT_LOW_LATENCY | `[513]` | 0…1 | read/write |
| `SMudo` | SETMEM_UNDEROVER | `[513]` | 0…1 | read/write |
| `SMain` | SETMEM_ASPECT_IN | `[513]` | 0…6 | read/write |
| `SMaou` | SETMEM_ASPECT_OUT | `[513]` | 0…3 | read/write |
| `SMpcr` | SETMEM_CROP_PREDEF | `[513]` | 0…4 | read/write |
| `SMchs` | SETMEM_CROP_LEFT | `[513]` | 0…4095 | read/write |
| `SMcvs` | SETMEM_CROP_TOP | `[513]` | 0…4095 | read/write |
| `SMche` | SETMEM_CROP_RIGHT | `[513]` | 0…4095 | read/write |
| `SMcve` | SETMEM_CROP_BOTTOM | `[513]` | 0…4095 | read/write |
| `SMcmo` | SETMEM_CRE_MODE | `[513]` | 0…4 | read/write |
| `SMcma` | SETMEM_CRE_MASK | `[513]` | 0…2 | read/write |
| `SMcin` | SETMEM_CRE_INVERT | `[513]` | 0…1 | read/write |
| `SMcrh` | SETMEM_CRE_REF_H | `[513]` | 0…359 | read/write |
| `SMcrs` | SETMEM_CRE_REF_S | `[513]` | 0…255 | read/write |
| `SMcrl` | SETMEM_CRE_REF_L | `[513]` | 0…255 | read/write |
| `SMcoh` | SETMEM_CRE_OFFSET_H | `[513]` | 0…255 | read/write |
| `SMcos` | SETMEM_CRE_OFFSET_S | `[513]` | 0…255 | read/write |
| `SMcol` | SETMEM_CRE_OFFSET_L | `[513]` | 0…255 | read/write |
| `SMcog` | SETMEM_CRE_OFFSET_GLOBAL | `[513]` | 0…255 | read/write |
| `SMcch` | SETMEM_CRE_COEF_H | `[513]` | 0…255 | read/write |
| `SMccs` | SETMEM_CRE_COEF_S | `[513]` | 0…255 | read/write |
| `SMccL` | SETMEM_CRE_COEF_L | `[513]` | 0…255 | read/write |
| `SMcah` | SETMEM_CRE_ASPECT_H | `[513]` | 0…175 | read/write |
| `SMcas` | SETMEM_CRE_ASPECT_S | `[513]` | 0…175 | read/write |
| `SMcde` | SETMEM_CRE_DSK_ENABLE | `[513]` | 0…1 | read/write |
| `SMcda` | SETMEM_CRE_DSK_ALPHA | `[513]` | 0…255 | read/write |
| `SMcrt` | SETMEM_CREV_REF_TINT | `[513]` | 0…359 | read/write |
| `SMcaa` | SETMEM_CREV_ALPHA_ANGLE | `[513]` | 1…180 | read/write |
| `SMcca` | SETMEM_CREV_COLOR_ANGLE | `[513]` | 1…180 | read/write |
| `SMcga` | SETMEM_CREV_GAIN | `[513]` | 0…4095 | read/write |
| `SMcof` | SETMEM_CREV_OFFSET | `[513]` | 0…255 | read/write |
| `SMsha` | SETMEM_SHARPNESS | `[513]` | 0…2 | read/write |
| `SMage` | SETMEM_AGE_COUNTER | `[513]` | 0…4294967295 | read/write |
| `SMalu` | SETMEM_AGE_LAST_USED | `[513]` | 0…4294967295 | read/write |
| `SMval` | SETMEM_IS_VALID | `[513]` | 0…1 | read/write |
| `SMupd` | SETMEM_UPDATE | `[513]` | 0…1 | read/write |

## LARGE_STILLS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `LSsrc` | LG_ST_SOURCE | `[8]` | 0…100 | read/write |
| `LSava` | LG_ST_AVAILABLE | `[8]` | 0…1 | read/write |
| `LSusd` | LG_ST_USED | `[8]` | 0…1 | read/write |
| `LSval` | LG_ST_VALID | `[8]` | 0…1 | read/write |
| `LSdua` | LG_ST_DUAL_CONFIG | `[8]` | 0…2 | read/write |
| `LSdst` | LG_ST_DUAL_STILL | `[8]` | 0…7 | read/write |
| `LSnat` | LG_ST_IS_NATIVE | `[8]` | 0…1 | read/write |
| `LSadd` | LG_ST_IMAGE_ADDRESS | `[8]` | 0…134217727 | read/write |
| `LSwid` | LG_ST_IMAGE_WIDTH | `[8]` | 0…2048 | read/write |
| `LShei` | LG_ST_IMAGE_HEIGHT | `[8]` | 0…2160 | read/write |
| `LSstr` | LG_ST_IMAGE_STRIDE | `[8]` | 0…16384 | read/write |
| `LSecf` | LG_ST_ENABLE_CROP_FINDER | `[8]` | 0…1 | read/write |
| `LScrl` | LG_ST_CROP_LEFT | `[8]` | 0…4095 | read/write |
| `LScrr` | LG_ST_CROP_RIGHT | `[8]` | 0…4095 | read/write |
| `LScrt` | LG_ST_CROP_TOP | `[8]` | 0…4095 | read/write |
| `LScrb` | LG_ST_CROP_BOTTOM | `[8]` | 0…4095 | read/write |
| `LScrp` | LG_ST_CROP_PREDEF | `[8]` | 0…4 | read/write |
| `LSain` | LG_ST_ASPECT_IN | `[8]` | 0…6 | read/write |
| `LSaou` | LG_ST_ASPECT_OUT | `[8]` | 0…3 | read/write |
| `LShdc` | LG_ST_IS_HDCP | `[8]` | 0…1 | read/write |
| `LSupd` | LG_ST_UPDATE | `[8]` | 0…1 | read/write |
| `LSdwi` | LG_ST_DISPLAY_WIDTH | `[8]` | 0…4096 | read-only |
| `LSdhe` | LG_ST_DISPLAY_HEIGHT | `[8]` | 0…2160 | read-only |

## REDUCED_STILLS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `RSsrc` | RD_ST_SOURCE | `[8]` | 0…100 | read/write |
| `RSava` | RD_ST_AVAILABLE | `[8]` | 0…1 | read/write |
| `RSusd` | RD_ST_USED | `[8]` | 0…1 | read/write |
| `RSval` | RD_ST_VALID | `[8]` | 0…1 | read/write |
| `RSadd` | RD_ST_IMAGE_ADDRESS | `[8]` | 0…134217727 | read/write |
| `RSwid` | RD_ST_IMAGE_WIDTH | `[8]` | 0…2048 | read/write |
| `RShei` | RD_ST_IMAGE_HEIGHT | `[8]` | 0…2048 | read/write |
| `RSstr` | RD_ST_IMAGE_STRIDE | `[8]` | 0…8192 | read/write |
| `RSecf` | RD_ST_ENABLE_CROP_FINDER | `[8]` | 0…1 | read/write |
| `RScrl` | RD_ST_CROP_LEFT | `[8]` | 0…4095 | read/write |
| `RScrr` | RD_ST_CROP_RIGHT | `[8]` | 0…4095 | read/write |
| `RScrt` | RD_ST_CROP_TOP | `[8]` | 0…4095 | read/write |
| `RScrb` | RD_ST_CROP_BOTTOM | `[8]` | 0…4095 | read/write |
| `RScrp` | RD_ST_CROP_PREDEF | `[8]` | 0…4 | read/write |
| `RSain` | RD_ST_ASPECT_IN | `[8]` | 0…6 | read/write |
| `RSaou` | RD_ST_ASPECT_OUT | `[8]` | 0…3 | read/write |
| `RShdc` | RD_ST_IS_HDCP | `[8]` | 0…1 | read/write |
| `RSupd` | RD_ST_UPDATE | `[8]` | 0…1 | read/write |
| `RSdwi` | RD_ST_DISPLAY_WIDTH | `[8]` | 0…2048 | read/write |
| `RSdhe` | RD_ST_DISPLAY_HEIGHT | `[8]` | 0…2048 | read/write |

## STILLS_CAPTURE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `STcen` | ST_CAPTURE_START | — | 0…1 | read/write |
| `STcso` | ST_CAPTURE_SOURCE_REQUEST | — | 0…31 | read/write |
| `STcfe` | ST_CAPTURE_FINDER_ENABLE | — | 0…1 | read/write |
| `STcpx` | ST_CAPTURE_POS_X | — | 0…16384 | read/write |
| `STcpy` | ST_CAPTURE_POS_Y | — | 0…16384 | read/write |
| `STcwi` | ST_CAPTURE_WIDTH | — | 0…16384 | read/write |
| `STche` | ST_CAPTURE_HEIGHT | — | 0…16384 | read/write |
| `STcdo` | ST_CAPTURE_DONE | — | 0…1 | read-only |
| `STctw` | ST_CAPTURE_TOTAL_WIDTH | — | 0…16384 | read-only |
| `STcth` | ST_CAPTURE_TOTAL_HEIGHT | — | 0…12800 | read-only |

## STILLS_CAPTURE_SLOT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `STsox` | ST_CAPTURE_SLOT_OFFSET_X | `[8]` | 0…65535 | read-only |
| `STsoy` | ST_CAPTURE_SLOT_OFFSET_Y | `[8]` | 0…65535 | read-only |
| `STswi` | ST_CAPTURE_SLOT_WIDTH | `[8]` | 0…2048 | read-only |
| `STshe` | ST_CAPTURE_SLOT_HEIGHT | `[8]` | 0…2048 | read-only |
| `STsdo` | ST_CAPTURE_SLOT_DONE | `[8]` | 0…1 | read-only |
| `STsss` | ST_CAPTURE_SLOT_SOURCE_STATUS | `[8]` | 0…32 | read-only |

## SNAPSHOTS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SNdis` | SNAPSHOT_GLOBAL_DISABLE | — | 0…1 | read/write |
| `SNena` | SNAPSHOT_ENABLE | `[40]` | 0…1 | read/write |
| `SNlsz` | SNAPSHOT_LINE_SIZE | `[40]` | 128…512 | read/write |

## NATIVE_SET

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `NSsec` | NS_SET_CONFIG | `[8,9,8]` | 1…41 | read/write |
| `NSpos` | NS_SET_POSITION | `[8,9,8]` | 0…8 | read/write |
| `NSpva` | NS_SET_POSITION_VALIDITY | `[8,9,8]` | 0…65535 | read-only |
| `NSlcp` | NS_INPUT_COMPATIBILITY | `[8,42]` | 0…6 | read-only |

## PRESET_NATIVE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PNinp` | PN_INPUTSET | `[8,3]` | 0…8 | read/write |
| `PNalp` | PN_ALPHA | `[8,3]` | 0…256 | read/write |
| `PNbcr` | PN_COLOR_RED | `[8,3]` | 0…255 | read/write |
| `PNbcg` | PN_COLOR_GREEN | `[8,3]` | 0…255 | read/write |
| `PNbcb` | PN_COLOR_BLUE | `[8,3]` | 0…255 | read/write |
| `PNotr` | PN_CROSS_TRANSITION | `[8,3]` | 0…2 | read/write |
| `PNowa` | PN_CROSS_TRANSITION_WAY | `[8,3]` | 0…3 | read/write |
| `PNoso` | PN_CROSS_START_OFFSET | `[8,3]` | 0…65535 | read/write |
| `PNoeo` | PN_CROSS_END_OFFSET | `[8,3]` | 0…65535 | read/write |

## PRESET_ID

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PIpid` | PI_PRESET_ID | `[8,3]` | 0…255 | read/write |
| `PIwur` | PI_WAS_UNMODIFIED_REQUEST | `[8,3]` | 1…1 | read/write |
| `PIwus` | PI_WAS_UNMODIFIED_STATUS | `[8,3]` | 0…1 | read-only |

## PRESET

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PRinp` | PE_INPUTNUM | `[8,3,24]` | 0…41 | read/write |
| `PRlay` | PE_LAYER_SELECTED | `[8,3,24]` | 0…1 | read/write |
| `PRaov` | PE_ASPECT_OVERRIDE | `[8,3,24]` | 0…4 | read/write |
| `PRflg` | PE_FLAGS | `[8,3,24]` | 0…2147483647 | read/write |
| `PRmcv` | PE_MASK_CURVE | `[8,3,24]` | 0…4294967295 | read/write |
| `PRalp` | PE_ALPHA | `[8,3,24]` | 0…256 | read/write |
| `PRpoh` | PE_POSH | `[8,3,24]` | 0…131072 | read/write |
| `PRpov` | PE_POSV | `[8,3,24]` | 0…131072 | read/write |
| `PRpoz` | PE_POSZ | `[8,3,24]` | 0…131072 | read/write |
| `PRsih` | PE_SIZEH | `[8,3,24]` | 0…65535 | read/write |
| `PRsiv` | PE_SIZEV | `[8,3,24]` | 0…65535 | read/write |
| `PRroh` | PE_ROTH | `[8,3,24]` | 0…65535 | read/write |
| `PRrov` | PE_ROTV | `[8,3,24]` | 0…65535 | read/write |
| `PRroz` | PE_ROTZ | `[8,3,24]` | 0…65535 | read/write |
| `PRcph` | PE_CROP_WIN_POS_H | `[8,3,24]` | 0…65535 | read/write |
| `PRcpv` | PE_CROP_WIN_POS_V | `[8,3,24]` | 0…65535 | read/write |
| `PRcsh` | PE_CROP_WIN_SIZE_H | `[8,3,24]` | 0…58981 | read/write |
| `PRcsv` | PE_CROP_WIN_SIZE_V | `[8,3,24]` | 0…58981 | read/write |
| `PRbst` | PE_BORDER_STYLE | `[8,3,24]` | 0…5 | read/write |
| `PRbcr` | PE_BORDER_COLOR_RED | `[8,3,24]` | 0…255 | read/write |
| `PRbcg` | PE_BORDER_COLOR_GREEN | `[8,3,24]` | 0…255 | read/write |
| `PRbcb` | PE_BORDER_COLOR_BLUE | `[8,3,24]` | 0…255 | read/write |
| `PRbal` | PE_BORDER_ALPHA | `[8,3,24]` | 0…255 | read/write |
| `PRbsh` | PE_BORDER_SIZE_H | `[8,3,24]` | 0…127 | read/write |
| `PRbsv` | PE_BORDER_SIZE_V | `[8,3,24]` | 0…127 | read/write |
| `PRotr` | PE_OPENING_TRANSITION | `[8,3,24]` | 0…7 | read/write |
| `PRowa` | PE_OPENING_TRANSITION_WAY | `[8,3,24]` | 0…10 | read/write |
| `PRctr` | PE_CLOSING_TRANSITION | `[8,3,24]` | 0…7 | read/write |
| `PRcwa` | PE_CLOSING_TRANSITION_WAY | `[8,3,24]` | 0…10 | read/write |
| `PRbah` | PE_BEZIER_PT1_POSH | `[8,3,24]` | 0…65535 | read/write |
| `PRbav` | PE_BEZIER_PT1_POSV | `[8,3,24]` | 0…65535 | read/write |
| `PRbaz` | PE_BEZIER_PT1_POSZ | `[8,3,24]` | 0…65535 | read/write |
| `PRbbh` | PE_BEZIER_PT2_POSH | `[8,3,24]` | 0…65535 | read/write |
| `PRbbv` | PE_BEZIER_PT2_POSV | `[8,3,24]` | 0…65535 | read/write |
| `PRbbz` | PE_BEZIER_PT2_POSZ | `[8,3,24]` | 0…65535 | read/write |
| `PRoso` | PE_OPENING_START_OFFSET | `[8,3,24]` | 0…65535 | read/write |
| `PRoeo` | PE_OPENING_END_OFFSET | `[8,3,24]` | 0…65535 | read/write |
| `PRcso` | PE_CLOSING_START_OFFSET | `[8,3,24]` | 0…65535 | read/write |
| `PRceo` | PE_CLOSING_END_OFFSET | `[8,3,24]` | 0…65535 | read/write |
| `PRtba` | PE_TBAR_BEZIER_PT1 | `[8,3,24]` | 0…255 | read/write |
| `PRtbb` | PE_TBAR_BEZIER_PT2 | `[8,3,24]` | 0…255 | read/write |

## PRESET_STATUS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SLinp` | PE_INPUTNUM_STATUS | `[8,3,24]` | 0…41 | read-only |
| `SLstu` | SCREENLAYER_STATUS_UP | `[8,24]` | 0…7 | read-only |
| `SLstd` | SCREENLAYER_STATUS_DOWN | `[8,24]` | 0…7 | read-only |
| `SLldu` | SCREENLAYER_LAYER_DEST_UP | `[8,24]` | 0…48 | read-only |
| `SLldd` | SCREENLAYER_LAYER_DEST_DOWN | `[8,24]` | 0…48 | read-only |

## MASTER_ALPHA

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `MAsna` | SCREENNATIVE_ALPHA | `[8]` | 0…255 | read/write |
| `MAnfa` | SCREENNATIVE_FADE_AUTO | `[8]` | 0…2 | read/write |
| `MAnas` | SCREENNATIVE_ALPHA_STATUS | `[8]` | 0…3 | read/write |
| `MAsla` | SCREENLAYER_ALPHA | `[8,24]` | 0…255 | read/write |
| `MAsfa` | SCREENLAYER_FADE_AUTO | `[8,24]` | 0…2 | read/write |
| `MAsas` | SCREENLAYER_ALPHA_STATUS | `[8,24]` | 0…3 | read/write |
| `MAmfa` | SCREEN_MASTER_FADE_AUTO | `[8]` | 0…2 | read/write |
| `MAfat` | FADE_AUTO_TIME | — | 0…100 | read/write |

## STROBE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `STsls` | SCREENLAYER_STROBE | `[8,24]` | 0…60 | read/write |

## GROUP_CONTROL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `GCtba` | TBAR | `[16]` | 0…65535 | read/write |
| `GCtku` | TAKE_UP | `[16]` | 0…1 | read/write |
| `GCtkd` | TAKE_DOWN | `[16]` | 0…1 | read/write |
| `GCtfr` | TAKE_FORCE | `[16]` | 1…1 | read/write |
| `GCtup` | TAKE_UP_TIME | `[16]` | 0…3000 | read/write |
| `GCtdn` | TAKE_DOWN_TIME | `[16]` | 0…3000 | read/write |
| `GCpup` | GROUP_UP | `[16]` | 0…2 | read/write |
| `GCpdn` | GROUP_DOWN | `[16]` | 0…2 | read/write |
| `GCprv` | GROUP_PREVIOUS | `[16]` | 0…2 | read/write |
| `GCupd` | GROUP_UPDATE | — | 1…1 | read/write |

## SEQ_TAKE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `STsta` | SEQ_TAKE | `[16]` | 0…255 | read/write |
| `STngr` | SEQ_NEXT_GROUP | `[16]` | 0…4 | read/write |

## GROUP_STUFF

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `GCstb` | GROUP_STEP_BACK | `[16]` | 0…1 | read/write |

## GROUP_STATUS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `GCsta` | GROUP_STATUS | `[16]` | 0…5 | read-only |
| `GCava` | GROUP_AVA | `[16]` | 0…1 | read-only |

## LAYER_SWAP

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `LSscr` | LS_SCREEN | — | 0…7 | read/write |
| `LSprs` | LS_PRESET | — | 0…2 | read/write |
| `LSlay` | LS_LAYER | — | 0…23 | read/write |
| `LSlow` | LS_LOWER | — | 0…1 | read/write |
| `LSrai` | LS_RAISE | — | 0…1 | read/write |

## CONFIGURATION

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `Plsgr` | SCREENLAYER_GROUP | `[8,24]` | 0…15 | read/write |
| `Plsgs` | SCREENLAYER_GROUP_STATUS | `[8,24]` | 0…15 | read-only |
| `Plngr` | SCREEN_GROUP | `[8]` | 0…15 | read/write |
| `Plngs` | SCREEN_GROUP_STATUS | `[8]` | 0…15 | read-only |

## PERSPECTIVE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PEsip` | SCREEN_IS_PERSPECTIVE | `[8]` | 0…1 | read/write |
| `PEszm` | SCREEN_IS_Z_MIXING | `[8]` | 0…1 | read/write |
| `PEsps` | SCREEN_IS_PERSPECTIVE_STATUS | `[8]` | 0…1 | read-only |
| `PEzms` | SCREEN_IS_Z_MIXING_STATUS | `[8]` | 0…1 | read-only |

## SCREEN_MIRROR

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SMmas` | SCREEN_MASTERSCREEN | `[8]` | 0…7 | read/write |
| `SMmen` | MIRROR_ENABLE | — | 0…1 | read/write |
| `SMlmm` | SCREENLAYER_MIRROR_MODE | `[8,24]` | 0…3 | read/write |
| `SMide` | SCREEN_MIRROR_IS_IDLE | — | 0…1 | read-only |

## SCREEN_LAYOUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SCsla` | SCREEN_LAYOUT | `[8]` | 0…1 | read/write |

## CONFIDENTIAL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `COlay` | SCREEN_CONFIDENTIAL_LAYOUT | `[8]` | 0…14 | read/write |
| `COsca` | SCREEN_CONFIDENTIAL_SOURCE_1 | `[8]` | 0…56 | read/write |
| `COscb` | SCREEN_CONFIDENTIAL_SOURCE_2 | `[8]` | 0…56 | read/write |
| `COscc` | SCREEN_CONFIDENTIAL_SOURCE_3 | `[8]` | 0…56 | read/write |
| `COscd` | SCREEN_CONFIDENTIAL_SOURCE_4 | `[8]` | 0…56 | read/write |
| `COsva` | SCREEN_CONFIDENTAL_IS_VALID | `[8]` | 0…1 | read-only |
| `COrec` | SCREEN_CONFIDENTIAL_RESOURCE_COUNT | `[8]` | 0…255 | read-only |
| `COrem` | SCREEN_CONFIDENTIAL_RESOURCE_MAX | `[8]` | 0…255 | read-only |
| `COupd` | CONFIDENTIAL_UPDATE | — | 1…1 | read/write |

## OUTPUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUava` | OUT_AVAILABLE | `[8]` | 0…1 | read-only |
| `OUuse` | OUT_USED | `[8]` | 0…1 | read/write |
| `OUena` | OUT_ENABLE | `[8]` | 0…1 | read-only |
| `OUbla` | OUT_BLACK | `[8]` | 0…1 | read/write |
| `OUduc` | OUT_DUAL_LINK_CAPABILITY | `[8]` | 0…3 | read-only |
| `OUkca` | OUT_4K_420_CAPABILITY | `[8]` | 0…1 | read-only |
| `OUfor` | OUT_FORMAT | `[8]` | 0…54 | read/write |
| `OUfst` | OUT_FORMAT_STATUS | `[8]` | 0…54 | read-only |
| `OUfle` | OUT_FORMAT_LOCK | `[8]` | 0…255 | read-only |
| `OUrat` | OUT_PREVIEW_RATE | `[8]` | 0…9 | read/write |
| `OUcts` | OUT_COMPUTER_TIMING_TYPE_STATUS | `[8]` | 0…3 | read-only |
| `OUsav` | OUT_SIGTYPEANALOG_VALIDITY | `[8,5]` | 0…2 | read-only |
| `OUsia` | OUT_SIGTYPEANALOG | `[8]` | 0…4 | read/write |
| `OUsid` | OUT_SIGTYPEDIGITAL | `[8]` | 0…2 | read/write |
| `OUmav` | OUT_PLUG_MODE_AVAILABLE | `[8]` | 0…1 | read-only |
| `OUpat` | OUT_PATTERN | `[8]` | 0…15 | read/write |
| `OUpgh` | OUT_PATTERN_GRID_NB_H | `[8]` | 1…255 | read/write |
| `OUpgv` | OUT_PATTERN_GRID_NB_V | `[8]` | 1…255 | read/write |
| `OUpsh` | OUT_PATTERN_HATCH_SIZE_H | `[8]` | 16…2048 | read/write |
| `OUpsv` | OUT_PATTERN_HATCH_SIZE_V | `[8]` | 16…2048 | read/write |
| `OUpgr` | OUT_PATTERN_SOLID_RED | `[8]` | 0…255 | read/write |
| `OUpre` | OUT_PATTERN_SOLID_GREEN | `[8]` | 0…255 | read/write |
| `OUpbl` | OUT_PATTERN_SOLID_BLUE | `[8]` | 0…255 | read/write |
| `OUpco` | OUT_PATTERN_COLOR_ENABLE | `[8]` | 0…3 | read/write |
| `OUhdc` | OUT_HDCP_ENABLE | `[8]` | 0…1 | read/write |
| `OUope` | OUT_OPTICAL_ENABLE | `[8]` | 0…1 | read/write |
| `OUopr` | OUT_OPTICAL_RESTART | `[8]` | 1…1 | read/write |
| `OUops` | OUT_OPTICAL_GLOBAL_STATUS | `[8]` | 0…5 | read-only |
| `OUopl` | OUT_OPTICAL_NB_LINK_STATUS | `[8]` | 0…2 | read-only |
| `OUopn` | OUT_OPTICAL_VENDOR_NAME | `[8,16]` | 0…255 | read-only |
| `OUopo` | OUT_OPTICAL_VENDOR_OUI | `[8,3]` | 0…255 | read-only |
| `OUopp` | OUT_OPTICAL_VENDOR_PN | `[8,16]` | 0…255 | read-only |
| `OUopa` | OUT_OPTICAL_ALARM_STATUS | `[8,2]` | 0…65535 | read-only |
| `OUopw` | OUT_OPTICAL_WARNING_STATUS | `[8,2]` | 0…65535 | read-only |
| `OUihc` | OUT_ISHDCP | `[8]` | 0…1 | read-only |
| `OUmod` | OUT_PLUG_MODE | `[8]` | 0…2 | read/write |
| `OUkin` | OUT_KIND | `[8]` | 2…3 | read-only |
| `OUshs` | OUT_SIZE_H_STATUS | `[8]` | 0…65535 | read-only |
| `OUsvs` | OUT_SIZE_V_STATUS | `[8]` | 0…65535 | read-only |
| `OUfva` | OUT_FORMAT_VALIDITY | `[8,55]` | 0…1 | read-only |
| `OUfrv` | OUT_FORMAT_RATE_VALIDITY | `[8]` | 0…1 | read-only |
| `OUpls` | OUT_PLUG_STATUS | `[8,4]` | 0…2 | read-only |
| `OUrov` | OUT_ROTATION_VALIDITY | `[8]` | 0…1 | read-only |
| `OPhul` | OUT_PREVIEW_HIDE_UNUSED_LAYERS | `[8]` | 0…1 | read/write |
| `OPcp` | OUT_PREVIEW_CLEAN_PREVIEW | `[8]` | 0…1 | read/write |

## OUTPUT_AOI_SIZE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OSaoi` | OUT_AOI_SIZE_MODE | `[8]` | 0…1 | read/write |
| `OSocp` | OUT_AOI_SIZE_OVERSCAN_COMP | `[8]` | 0…20 | read/write |
| `OSash` | OUT_AOI_SIZE_CUSTOM_WIDTH_H | `[8]` | 0…100000 | read/write |
| `OSasv` | OUT_AOI_SIZE_CUSTOM_WIDTH_V | `[8]` | 0…100000 | read/write |
| `OSaph` | OUT_AOI_SIZE_CUSTOM_POS_H | `[8]` | 0…100000 | read/write |
| `OSapv` | OUT_AOI_SIZE_CUSTOM_POS_V | `[8]` | 0…100000 | read/write |
| `OSaup` | OUT_AOI_SIZE_UPDATE | `[8]` | 0…1 | read/write |

## OUTPUT_AOI_STATUS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OSsmh` | OUT_AOI_STATUS_MAX_SIZE_H | `[8]` | 0…65535 | read-only |
| `OSsmv` | OUT_AOI_STATUS_MAX_SIZE_V | `[8]` | 0…65535 | read-only |
| `OSfmh` | OUT_AOI_STATUS_FORMAT_POS_H | `[8]` | 0…65535 | read-only |
| `OSfmv` | OUT_AOI_STATUS_FORMAT_POS_V | `[8]` | 0…65535 | read-only |
| `OSSsh` | OUT_AOI_STATUS_SIZE_H | `[8]` | 0…65535 | read-only |
| `OSSsv` | OUT_AOI_STATUS_SIZE_V | `[8]` | 0…65535 | read-only |
| `OSSph` | OUT_AOI_STATUS_POS_H | `[8]` | 0…65535 | read-only |
| `OSSpv` | OUT_AOI_STATUS_POS_V | `[8]` | 0…65535 | read-only |
| `OSsro` | OUT_AOI_STATUS_ROTATION | `[8]` | 0…4 | read-only |

## OUTPUT_AUTOCALIB

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUaou` | OUT_AUTOCALIB_OUTPUT | `[8]` | 0…1 | read/write |
| `OUaos` | OUT_AUTOCALIB_OUTPUT_SUCCEED | `[8]` | 0…1 | read-only |
| `OUaop` | OUT_AUTOCALIB_OUTPUT_PROGRESS | `[8]` | 0…100 | read-only |

## FORMATS_COMPUTER_CUSTOM_COMPUTE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OCcrb` | OCCOMPUTE_CVT_REDUCED_BLK | — | 0…1 | read/write |
| `OCfhs` | OCCOMPUTE_FULL_HSYNC | — | 32…500 | read/write |
| `OCfpo` | OCCOMPUTE_FULL_HSYNC_POL | — | 0…1 | read/write |
| `OCfhb` | OCCOMPUTE_FULL_HBACKPORCH | — | 32…1000 | read/write |
| `Ocfhf` | OCCOMPUTE_FULL_HFRONTPORCH | — | 8…3000 | read/write |
| `OCfhu` | OCCOMPUTE_FULL_HUTIL | — | 200…4096 | read/write |
| `OCfht` | OCCOMPUTE_FULL_HTOTAL_STATUS | — | 0…65535 | read-only |
| `OCfvs` | OCCOMPUTE_FULL_VSYNC | — | 2…20 | read/write |
| `OCfvp` | OCCOMPUTE_FULL_VSYNC_POL | — | 0…1 | read/write |
| `OCfvb` | OCCOMPUTE_FULL_VBACKPORCH | — | 4…1000 | read/write |
| `OCfvf` | OCCOMPUTE_FULL_VFRONTPORCH | — | 1…50 | read/write |
| `OCfvu` | OCCOMPUTE_FULL_VUTIL | — | 200…2160 | read/write |
| `OCfvt` | OCCOMPUTE_FULL_VTOTAL_STATUS | — | 0…65535 | read-only |
| `OCfra` | OCCOMPUTE_FULL_RATE | — | 22000…75000 | read/write |
| `OCfrs` | OCCOMPUTE_FULL_RATE_STATUS | — | 22000…75000 | read-only |
| `OCfsc` | OCCOMPUTE_FULL_SCANTYPE | — | 0…3 | read/write |
| `OCcty` | OCCOMPUTE_TYPE | — | 0…1 | read/write |
| `OCcap` | OCCOMPUTE_CAPTION | `[20]` | 0…255 | read/write |
| `OCccr` | OCCOMPUTE_CHECK_REQUEST | — | 0…1 | read/write |
| `OCcsw` | OCCOMPUTE_STATUS_WARNING | — | 0…255 | read-only |
| `OCcse` | OCCOMPUTE_STATUS_ERROR | — | 0…65535 | read-only |
| `Occst` | OCCOMPUTE_STATUS | — | 0…3 | read-only |
| `OCloa` | OCCOMPUTE_LOAD | `[10]` | 0…1 | read/write |
| `OCcsa` | OCCOMPUTE_SAVE | `[10]` | 0…1 | read/write |
| `OCrst` | OCCOMPUTE_RESET | — | 0…1 | read/write |

## FORMATS_COMPUTER_CUSTOM

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OCadv` | OCFORMAT_TYPE | `[10]` | 0…1 | read/write |
| `OCnam` | OCFORMAT_NAME | `[10,20]` | 0…255 | read/write |
| `OCfca` | OCFORMAT_CAPTION | `[10,20]` | 0…255 | read/write |
| `OCrdb` | OCFORMAT_REDUCED_BLANKINGS | `[10]` | 0…1 | read/write |
| `Ochsy` | OCFORMAT_HSYNC | `[10]` | 32…500 | read/write |
| `OCsyh` | OCFORMAT_HSYNC_POL | `[10]` | 0…1 | read/write |
| `OChbp` | OCFORMAT_HBACKPORCH | `[10]` | 32…1000 | read/write |
| `OChfp` | OCFORMAT_HFRONTPORCH | `[10]` | 8…3000 | read/write |
| `Ochut` | OCFORMAT_HUTIL | `[10]` | 200…4096 | read/write |
| `OChto` | OCFORMAT_HTOTAL | `[10]` | 0…65535 | read/write |
| `OCvsy` | OCFORMAT_VSYNC | `[10]` | 2…20 | read/write |
| `OCsyv` | OCFORMAT_VSYNC_POL | `[10]` | 0…1 | read/write |
| `OCvbp` | OCFORMAT_VBACKPORCH | `[10]` | 4…1000 | read/write |
| `OCvfp` | OCFORMAT_VFRONTPORCH | `[10]` | 1…50 | read/write |
| `OCvua` | OCFORMAT_VUTIL | `[10]` | 200…2160 | read/write |
| `OCvto` | OCFORMAT_VTOTAL | `[10]` | 0…65535 | read/write |
| `Ocrat` | OCFORMAT_RATE | `[10]` | 22000…75000 | read/write |
| `OCsct` | OCFORMAT_SCANTYPE | `[10]` | 0…3 | read/write |
| `OCstw` | OCFORMAT_STATUS_WARNING | `[10]` | 0…255 | read-only |
| `OCste` | OCFORMAT_STATUS_ERROR | `[10]` | 0…65535 | read-only |
| `Ocset` | OCFORMAT_WAS_SETTED | `[10]` | 0…1 | read/write |
| `OCdel` | OCFORMAT_DELETE | `[10]` | 0…1 | read/write |
| `Ocupd` | OCFORMAT_UPDATE | — | 0…1 | read/write |

## OUTPUT_CONTROL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OCfli` | OUT_FLICK | `[8]` | 0…7 | read/write |
| `OCcor` | OUT_CORING_LEVEL | `[8]` | 0…255 | read/write |
| `OCgam` | OUT_GAMMA | `[8]` | 5…40 | read/write |
| `OCbri` | OUT_BRIGHTNESS | `[8]` | 0…255 | read/write |
| `OCcon` | OUT_CONTRAST | `[8]` | 0…255 | read/write |
| `OCgre` | OUT_GAIN_RED | `[8]` | 0…255 | read/write |
| `OCggr` | OUT_GAIN_GREEN | `[8]` | 0…255 | read/write |
| `OCgbl` | OUT_GAIN_BLUE | `[8]` | 0…255 | read/write |

## SCREEN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SCtyp` | OSCREEN_TYPE | `[8]` | 0…1 | read/write |
| `SCico` | OSCREEN_IS_CONFIDENCIAL | `[8]` | 0…1 | read/write |
| `SCpat` | OSCREEN_PATTERN | `[8]` | 0…14 | read/write |
| `SCpav` | OSCREEN_PATTERN_AVAILABLE | `[8,16]` | 0…1 | read-only |
| `SCpgh` | OSCREEN_PATTERN_GRID_NB_H | `[8]` | 1…255 | read/write |
| `SCpgv` | OSCREEN_PATTERN_GRID_NB_V | `[8]` | 1…255 | read/write |
| `SCpsh` | OSCREEN_PATTERN_HATCH_SIZE_H | `[8]` | 16…2048 | read/write |
| `SCpsv` | OSCREEN_PATTERN_HATCH_SIZE_V | `[8]` | 16…2048 | read/write |
| `SCpgr` | OSCREEN_PATTERN_SOLID_RED | `[8]` | 0…255 | read/write |
| `SCpre` | OSCREEN_PATTERN_SOLID_GREEN | `[8]` | 0…255 | read/write |
| `SCpbl` | OSCREEN_PATTERN_SOLID_BLUE | `[8]` | 0…255 | read/write |
| `SCpco` | OSCREEN_PATTERN_COLOR_ENABLE | `[8]` | 0…3 | read/write |
| `SCcvh` | OSCREEN_COVERING_SIZE_H | `[8,15]` | 0…2047 | read/write |
| `SCcvv` | OSCREEN_COVERING_SIZE_V | `[8,15]` | 0…2047 | read/write |
| `SCsih` | OSCREEN_SIZE_H | `[8]` | 1…16 | read/write |
| `SCsiv` | OSCREEN_SIZE_V | `[8]` | 1…16 | read/write |
| `SCshs` | OSCREEN_SIZE_H_STATUS | `[8]` | 1…16 | read-only |
| `SCsvs` | OSCREEN_SIZE_V_STATUS | `[8]` | 1…16 | read-only |
| `SCfrh` | OSCREEN_FREE_SIZE_H | `[8]` | 0…65536 | read/write |
| `SCfrv` | OSCREEN_FREE_SIZE_V | `[8]` | 0…65536 | read/write |
| `SCssh` | OSCREEN_STATUS_SIZE_H | `[8]` | 0…65536 | read-only |
| `SCssv` | OSCREEN_STATUS_SIZE_V | `[8]` | 0…65536 | read-only |
| `SCmly` | OSCREEN_MAX_LAYERS | `[8]` | 0…24 | read-only |

## OUTPUT_SCREEN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OSren` | OSCREEN_ROTATION_ENABLE | `[8]` | 0…1 | read/write |
| `OSrot` | OSCREEN_OUT_ROTATION | `[8]` | 0…4 | read/write |
| `OSsou` | OSCREEN_OUT | `[8]` | 0…7 | read/write |
| `OSomo` | OSCREEN_OUT_MODE | `[8]` | 0…1 | read/write |
| `OSpre` | OSCREEN_OUT_PREVIEW_AVAILABLE | `[8]` | 0…1 | read-only |
| `OSipo` | OSCREEN_OUT_IS_PREVIEW_OF | `[8]` | 0…7 | read/write |
| `OSdue` | OSCREEN_OUT_DUAL_ENABLE | `[8]` | 0…1 | read/write |
| `OSken` | OSCREEN_OUT_4K_420_ENABLE | `[8]` | 0…1 | read/write |
| `OSors` | OSCREEN_OUT_RESOURCES | `[8]` | 0…4 | read/write |
| `OSupd` | OSCREEN_OUT_GLOBAL_UPDATE | — | 0…1 | read/write |
| `OScer` | OSCREEN_OUT_CONFIG_ERROR | — | 0…1 | read-only |
| `OSpoh` | OSCREEN_OUT_POS_H | `[8]` | 1…16 | read/write |
| `OSpov` | OSCREEN_OUT_POS_V | `[8]` | 1…16 | read/write |
| `OSfph` | OSCREEN_FREE_OUT_POS_H | `[8]` | 0…65536 | read/write |
| `OSfpv` | OSCREEN_FREE_OUT_POS_V | `[8]` | 0…65536 | read/write |
| `OSsph` | OSCREEN_STATUS_FREE_OUT_POS_H | `[8]` | 0…65536 | read-only |
| `OSspv` | OSCREEN_STATUS_FREE_OUT_POS_V | `[8]` | 0…65536 | read-only |

## SOFTEDGE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SEcen` | SOFTEDGE_CURVE_ENABLE | `[8,4]` | 0…1 | read/write |
| `SEadv` | SOFTEDGE_ADVANCED | `[8,4]` | 0…1 | read/write |
| `SEapc` | SOFTEDGE_ADVANCED_POINT_COUNT | `[8,4]` | 0…10 | read/write |
| `SEpoi` | SOFTEDGE_POINT | `[8,4,10,2]` | 462…817 | read/write |
| `SEbof` | SOFTEDGE_BLACK_OFFSET | `[8,4]` | 0…1023 | read/write |
| `SEbrl` | SOFTEDGE_BLACK_R_LEVEL | `[8,2]` | 0…127 | read/write |
| `SEblg` | SOFTEDGE_BLACK_G_LEVEL | `[8,2]` | 0…127 | read/write |
| `SEbbl` | SOFTEDGE_BLACK_B_LEVEL | `[8,2]` | 0…127 | read/write |

## MONITORING__OUTPUTS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `MOava` | MOUT_AVAILABLE | `[2]` | 0…1 | read-only |
| `MOena` | MOUT_ENABLE | `[2]` | 0…1 | read-only |
| `MOduc` | MOUT_DUAL_LINK_CAPABILITY | `[2]` | 0…1 | read-only |
| `MOfor` | MOUT_FORMAT | `[2]` | 0…54 | read/write |
| `MOfst` | MOUT_FORMAT_STATUS | `[2]` | 0…54 | read-only |
| `MOfle` | MOUT_FORMAT_LOCK | `[2]` | 0…255 | read-only |
| `MOrat` | MOUT_RATE | `[2]` | 0…11 | read/write |
| `MOcts` | MOUT_COMPUTER_TIMING_TYPE_STATUS | `[2]` | 0…3 | read-only |
| `MOsav` | MOUT_SIGTYPEANALOG_VALIDITY | `[2,5]` | 0…2 | read-only |
| `MOsia` | MOUT_SIGTYPEANALOG | `[2]` | 0…4 | read/write |
| `MOycc` | MOUT_YC_COMPOSITE_ENABLE | `[2]` | 0…1 | read/write |
| `MOsid` | MOUT_SIGTYPEDIGITAL | `[2]` | 0…2 | read/write |
| `MOpat` | MOUT_PATTERN | `[2]` | 0…15 | read/write |
| `MOpgh` | MOUT_PATTERN_GRID_NB_H | `[2]` | 1…255 | read/write |
| `MOpgv` | MOUT_PATTERN_GRID_NB_V | `[2]` | 1…255 | read/write |
| `MOpsh` | MOUT_PATTERN_HATCH_SIZE_H | `[2]` | 16…2048 | read/write |
| `MOpsv` | MOUT_PATTERN_HATCH_SIZE_V | `[2]` | 16…2048 | read/write |
| `MOpgr` | MOUT_PATTERN_SOLID_RED | `[2]` | 0…255 | read/write |
| `MOpre` | MOUT_PATTERN_SOLID_GREEN | `[2]` | 0…255 | read/write |
| `MOpbl` | MOUT_PATTERN_SOLID_BLUE | `[2]` | 0…255 | read/write |
| `MOpco` | MOUT_PATTERN_COLOR_ENABLE | `[2]` | 0…3 | read/write |
| `MOhdc` | MOUT_HDCP_ENABLE | `[2]` | 0…1 | read/write |
| `MOihc` | MOUT_ISHDCP | `[2]` | 0…1 | read/write |
| `MOios` | MOUT_IMAGE_OVERSCAN | `[2]` | 0…1 | read/write |
| `MOiph` | MOUT_IMAGE_ADJUST_POS_H | `[2]` | 0…255 | read/write |
| `MOipv` | MOUT_IMAGE_ADJUST_POS_V | `[2]` | 0…255 | read/write |
| `MOish` | MOUT_IMAGE_ADJUST_SIZE_H | `[2]` | 0…255 | read/write |
| `MOisv` | MOUT_IMAGE_ADJUST_SIZE_V | `[2]` | 0…255 | read/write |
| `MObcr` | MOUT_BACKGROUND_COLOR_R | `[2]` | 0…255 | read/write |
| `MObcg` | MOUT_BACKGROUND_COLOR_G | `[2]` | 0…255 | read/write |
| `MObcb` | MOUT_BACKGROUND_COLOR_B | `[2]` | 0…255 | read/write |
| `MOfli` | MOUT_FLICK | `[2]` | 0…7 | read/write |
| `MOcor` | MOUT_CORING_LEVEL | `[2]` | 0…255 | read/write |
| `MOgam` | MOUT_GAMMA | `[2]` | 5…40 | read/write |
| `MOkin` | MOUT_KIND | `[2]` | 0…3 | read-only |
| `MOshs` | MOUT_SIZE_H_STATUS | `[2]` | 0…65535 | read-only |
| `MOsvs` | MOUT_SIZE_V_STATUS | `[2]` | 0…65535 | read-only |
| `MOfva` | MOUT_FORMAT_VALIDITY | `[2,55]` | 0…1 | read-only |
| `MOfrv` | MOUT_FORMAT_RATE_VALIDITY | `[2]` | 0…1 | read-only |
| `MOpls` | MOUT_PLUG_STATUS | `[2,3]` | 0…2 | read-only |
| `MOhul` | MOUT_HIDE_UNUSED_LAYERS | `[2]` | 0…1 | read/write |
| `MOcpr` | MOUT_CLEAN_PREVIEW | `[2]` | 0…1 | read/write |
| `MOsom` | MOUT_SHOW_ONLY_MY_OUTPUTS | `[2]` | 0…1 | read/write |

## MONITORING_SCREEN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `MSsih` | MOSCREEN_SIZE_H | — | 1…2 | read/write |
| `MSsiv` | MOSCREEN_SIZE_V | — | 1…2 | read/write |

## MONITOING_OUTPUT_SCREEN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `MSpoh` | MOSCREEN_OUT_POS_H | `[2]` | 1…2 | read/write |
| `MSpov` | MOSCREEN_OUT_POS_V | `[2]` | 1…2 | read/write |
| `MSrec` | MOSCREEN_OUT_RESSOURCES_COUNT | `[2]` | 0…255 | read-only |
| `Msree` | MOSCREEN_OUT_RESSOURCES_PER_ELEMENT | `[2,12]` | 0…255 | read-only |
| `MSrem` | MOSCREEN_OUT_RESSOURCES_MAX | `[2]` | 0…255 | read-only |

## MONITORING_AUTOCALIB

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `MOaou` | MON_AUTOCALIB_OUTPUT | `[2]` | 0…1 | read/write |
| `MOaos` | MON_AUTOCALIB_OUTPUT_SUCCEED | `[2]` | 0…1 | read-only |
| `MOaop` | MON_AUTOCALIB_OUTPUT_PROGRESS | `[2]` | 0…100 | read-only |

## FRAMELOCK_INPUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `FIava` | FRMLCK_IN_AVAILABLE | `[2]` | 0…1 | read-only |
| `FIsyg` | FRMLCK_SYNCHRO_GROUP | `[2]` | 0…4 | read/write |
| `FIsyt` | FRMLCK_IN_SYNC_TYPE | `[2]` | 1…2 | read/write |
| `FIsyl` | FRMLCK_IN_SYNC_LOAD | `[2]` | 0…1 | read/write |
| `FIist` | FRMLCK_IN_COMPATIBLE_MODE | `[2]` | 0…1 | read/write |
| `FIvfr` | FRMLCK_IN_V_FREQ | `[2]` | 0…4294967295 | read-only |
| `FIhfr` | FRMLCK_IN_H_FREQ | `[2]` | 0…65535 | read-only |
| `FIval` | FRMLCK_IN_IS_VALID | `[2]` | 0…1 | read-only |

## EDID_IN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `EIava` | EDID_IN_AVAILABLE | `[24,6]` | 0…1 | read-only |
| `EIdat` | EDID_IN_DATA | `[24,6,256]` | 0…255 | read/write |
| `EIstr` | EDID_IN_STORE | `[24,6]` | 0…1 | read/write |
| `EIohc` | EDID_IN_ORIGIN_HASHCODE | `[24,6]` | 0…4294967295 | read/write |
| `EIhcd` | EDID_IN_HASHCODE | `[24,6]` | 0…4294967295 | read-only |
| `EIpfa` | EDID_IN_PREF_FORMAT_AVAILABLE | `[24,6,32]` | 0…255 | read-only |
| `EIspf` | EDID_IN_SET_PREF_FORMAT | `[24,6]` | 0…146 | read/write |
| `EIpfn` | EDID_IN_PREF_FORMAT_NAME | `[24,6,16]` | 0…255 | read-only |

## EDID_OUT

| Mnemonic | Reply | Name | Dims | Range | Access |
|---|---|---|---|---|---|
| `EOava` |  | EDID_OUT_AVAILABLE | `[8,4]` | 0…1 | read-only |
| `EOdat` |  | EDID_OUT_DATA | `[8,4,256]` | 0…255 | read-only |
| `EOval` | `EOsiv` | EDID_OUT_VALIDITY | `[8,4]` | 0…1 | read-only |
| `EOred` |  | EDID_OUT_READ | `[8,4]` | 0…1 | read/write |
| `EOhcd` |  | EDID_OUT_HASHCODE | `[8,4]` | 0…4294967295 | read-only |

## EDID_MONITORING

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `EMava` | EDID_MOUT_AVAILABLE | `[2,3]` | 0…1 | read-only |
| `EMdat` | EDID_MOUT_DATA | `[2,3,256]` | 0…255 | read-only |
| `EMval` | EDID_MOUT_VALIDITY | `[2,3]` | 0…1 | read-only |
| `EMred` | EDID_MOUT_READ | `[2,3]` | 0…1 | read/write |
| `EMhcd` | EDID_MOUT_HASHCODE | `[2,3]` | 0…4294967295 | read-only |

## INTERNAL__FRAME__RATE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `IRsel` | INT_FRM_RATE_SELECT | — | 0…4 | read/write |
| `IRsta` | INT_FRM_RATE_STATUS | — | 0…4 | read-only |
| `IRmar` | INT_FRM_RATE_MASTER_RATE | — | 0…7 | read/write |
| `IRfrf` | INT_FRM_RATE_FRAMELOCK_REF | — | 0…26 | read/write |
| `IRvfr` | INT_FRM_RATE_V_FREQ | — | 0…4294967295 | read-only |
| `IRrvf` | INT_FRM_RATE_REF_V_FREQ | — | 0…4294967295 | read-only |
| `IRrhf` | INT_FRM_RATE_REF_H_FREQ | — | 0…4294967295 | read-only |
| `IRrdi` | INT_FRM_RATE_REFIN_DIRECTLY | — | 0…1 | read-only |
| `IRval` | INT_FRM_RATE_SELECT_IS_VALID | — | 0…2 | read-only |
| `IRsyg` | INT_FRM_RATE_SYNC_GROUP | — | 0…4 | read-only |

## GPIO

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `GPiav` | GPIO_IN_AVAILABLE | `[2]` | 0…1 | read-only |
| `GPipo` | GPIO_IN_POLARITY | `[2]` | 0…1 | read/write |
| `GPist` | GPIO_IN_STATUS | `[2]` | 0…1 | read-only |
| `GPimo` | GPIO_IN_MODE | `[2]` | 0…1 | read/write |
| `GPits` | GPIO_IN_TAKE_SCREEN | `[2,8]` | 0…1 | read/write |
| `GPoav` | GPIO_OUT_AVAILABLE | `[10]` | 0…1 | read-only |
| `GPopo` | GPIO_OUT_POLARITY | `[10]` | 0…1 | read/write |
| `GPofa` | GPIO_OUT_COMMAND | `[10]` | 0…1 | read/write |
| `GPomo` | GPIO_OUT_MODE | `[10]` | 0…2 | read/write |
| `GPoti` | GPIO_OUT_TALLY_INPUT | `[10,8,42]` | 0…1 | read/write |

## TALLY

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `TAopr` | INPUT_ON_PROGRAM | `[42]` | 0…1 | read-only |
| `TAopw` | INPUT_ON_PREVIEW | `[42]` | 0…1 | read-only |

## TEMPERATURE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `TEcar` | TEMP_CARD | `[2,20]` | 0…65535 | read-only |
| `TEcal` | TEMP_CARD_ALARM | `[2,20]` | 0…2 | read-only |
| `TEfga` | TEMP_FPGA | `[2,14,2]` | 0…65535 | read-only |
| `TEfal` | TEMP_FPGA_ALARM | `[2,14,2]` | 0…2 | read-only |
| `TEref` | TEMP_REFRESH | — | 0…1 | read/write |
| `TEdal` | TEMP_DEVICE_ALARM | `[2]` | 0…2 | read-only |
| `TEdao` | TEMP_DEVICE_ALARM_OVERRIDE | — | 0…1 | read/write |

## FAN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `FAfga` | FAN_SPEED_FPGA | `[2,14,2]` | 0…65535 | read-only |
| `FAfal` | FAN_SPEED_FPGA_ALARM | `[2,14,2]` | 0…1 | read-only |
| `FAcas` | FAN_SPEED_CASE | `[2,10]` | 0…65535 | read-only |
| `FAcal` | FAN_SPEED_CASE_ALARM | `[2,10]` | 0…1 | read-only |
| `FAref` | FAN_REFRESH | — | 0…1 | read/write |
| `FAalm` | FAN_DEVICE_ALARM | `[2]` | 0…1 | read-only |

## COUPLING

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `COcmo` | COUPLING_MODE | — | 0…4 | read/write |
| `COcst` | COUPLING_STATUS | — | 0…5 | read-only |
| `COcpr` | COUPLING_PROGRESS | — | 0…5 | read-only |
| `COcab` | COUPLING_ABORT | — | 0…1 | read/write |
| `COcsr` | COUPLING_SESSION_RESTART | — | 0…1 | read/write |
| `COcer` | COUPLING_ERROR | — | 0…5 | read-only |
| `COnid` | COUPLING_NETWORK_ID | — | 0…8 | read-only |
| `COaud` | COUPLING_DISABLE_AUTODOWNGRADE | — | 0…1 | read/write |
| `COdsm` | COUPLING_DETECT_SET_TO_MODE | — | 0…1 | read/write |
| `COdlp` | COUPLING_DETECT_PROGRESS | — | 0…6 | read-only |
| `COdls` | COUPLING_DETECT_STATUS | — | 0…5 | read-only |
| `COdli` | COUPLING_DETECT_LINK_REQUEST | — | 0…3 | read/write |
| `COdlv` | COUPLING_DETECT_LINK_VER_UPDATER | — | 0…4294967295 | read-only |
| `COdld` | COUPLING_DETECT_LINK_DEV | — | 0…119 | read-only |
| `COdlc` | COUPLING_DETECT_LINK_CABLE | `[3]` | 0…1 | read-only |
| `COdsn` | COUPLING_DETECT_LINK_DEVICE_SERIAL_NUM | — | 0…4294967295 | read-only |
| `COdss` | COUPLING_DETECT_LINK_DEVICE_STRING | `[4]` | 0…255 | read-only |
| `CSdsr` | COUPLING_DETECT_SYNC_REQUEST | — | 0…3 | read/write |
| `CSres` | COUPLING_DETECT_SYNC_RESET | — | 0…1 | read/write |
| `CScnt` | COUPLING_DETECT_SYNC_COUNT | — | 0…255 | read-only |
| `CSvup` | COUPLING_DETECT_SYNC_VER_UPDATER | `[9]` | 0…4294967295 | read-only |
| `CSdev` | COUPLING_DETECT_SYNC_DEV | `[9]` | 0…119 | read-only |
| `CSipf` | COUPLING_DETECT_SYNC_IP | `[9,4]` | 0…255 | read-only |
| `CSpos` | COUPLING_DETECT_SYNC_POSITION | `[9]` | 0…255 | read-only |
| `CSssr` | COUPLING_STILL_SHARE_CHECK_REQUEST | — | 0…1 | read/write |
| `CSscr` | COUPLING_STILL_SHARE_CHECK_STATUS | — | 0…1 | read/write |
| `CSsce` | COUPLING_STILL_SHARE_CHECK_ERROR | — | 0…255 | read/write |
| `CSssc` | COUPLING_STILL_SHARE_CHECK_COUNT | — | 0…65535 | read/write |
| `CSsae` | COUPLING_STILL_SHARE_AUTO_EXECUTE | — | 0…1 | read/write |
| `CSser` | COUPLING_STILL_SHARE_EXECUTE_REQUEST | — | 0…1 | read/write |
| `CSses` | COUPLING_STILL_SHARE_EXECUTE_STATUS | — | 0…1 | read/write |
| `CSsee` | COUPLING_STILL_SHARE_EXECUTE_ERROR | — | 0…255 | read/write |
| `CSsep` | COUPLING_STILL_SHARE_EXECUTE_PROGRESS | — | 0…65535 | read/write |
| `CSsec` | COUPLING_STILL_SHARE_EXECUTE_COUNT | — | 0…65535 | read/write |
