# Midra series — variable reference

Transport: **TCP 10500**, commands terminated `CRLF`, replies CRLF. See [framing](framing.md) and the [variable model](variable-model.md).

**562 variables** across **49 groups**. Each variable has a 5-character mnemonic (a few are 1-character), an index shape (`Dims`), an integer range, and read/write access. Replies use the same mnemonic except where a **Reply** column is shown.

## Groups

- [GRP_SYSTEM](#grp-system) (14)
- [GRP_LAN](#grp-lan) (8)
- [GRP_CONTROL](#grp-control) (34)
- [GRP_DEVICE_FLAGS](#grp-device-flags) (19)
- [GRP_DEVICE_INFO](#grp-device-info) (10)
- [GRP_STANDBY](#grp-standby) (7)
- [GRP_VERSION](#grp-version) (5)
- [GRP_INPUT](#grp-input) (20)
- [GRP_INPUT_AUTOSET](#grp-input-autoset) (6)
- [GRP_INPUT_AUTOCENTER](#grp-input-autocenter) (2)
- [GRP_INPUT_KEYING](#grp-input-keying) (7)
- [GRP_INPUT_SIGNALS](#grp-input-signals) (39)
- [GRP_INPUT_SETTINGS](#grp-input-settings) (36)
- [GRP_INPUT_SETTINGS_MEMORIES](#grp-input-settings-memories) (51)
- [GRP_PRESET_ID](#grp-preset-id) (3)
- [GRP_PRESET_ELEMENT](#grp-preset-element) (27)
- [GRP_PRESET_UPDATE](#grp-preset-update) (1)
- [GRP_PRESET_MEMORY](#grp-preset-memory) (31)
- [GRP_TAKE_CONTROL](#grp-take-control) (5)
- [GRP_PRESET_CONTROL](#grp-preset-control) (10)
- [GRP_OUTPUT](#grp-output) (8)
- [GRP_OUTPUT_FORMAT](#grp-output-format) (4)
- [GRP_OUTPUT_VALIDITY](#grp-output-validity) (2)
- [GRP_OUTPUT_MASTER](#grp-output-master) (1)
- [GRP_OUTPUT_FRAMELOCK](#grp-output-framelock) (5)
- [GRP_OUTPUT_SIGTYPE](#grp-output-sigtype) (5)
- [GRP_OUTPUT_STATUS](#grp-output-status) (9)
- [GRP_OUTPUT_PLUG_STATUS](#grp-output-plug-status) (5)
- [GRP_CUSTOM_COMPUTE](#grp-custom-compute) (24)
- [GRP_CUSTOM_FORMAT](#grp-custom-format) (17)
- [GRP_OUTPUT_CONTROL](#grp-output-control) (2)
- [GRP_VIDEO_OUT_FORMAT](#grp-video-out-format) (3)
- [GRP_VIDEO_OUT_VALIDITY](#grp-video-out-validity) (1)
- [GRP_VIDEO_OUT_STATUS](#grp-video-out-status) (8)
- [GRP_VIDEO_OUT](#grp-video-out) (14)
- [GRP_SCREEN](#grp-screen) (8)
- [GRP_SCREEN_CONFIG](#grp-screen-config) (5)
- [GRP_SOFTEDGE](#grp-softedge) (9)
- [GRP_EDID_IN](#grp-edid-in) (8)
- [GRP_EDID_OUT](#grp-edid-out) (5)
- [GRP_AUDIO_INPUT](#grp-audio-input) (14)
- [GRP_AUDIO_OUTPUT](#grp-audio-output) (13)
- [GRP_AUDIO_LEVELS](#grp-audio-levels) (2)
- [GRP_STILL_PIX](#grp-still-pix) (14)
- [GRP_STILL_PIX_CAPTURE](#grp-still-pix-capture) (22)
- [GRP_OSD](#grp-osd) (2)
- [GRP_RTC](#grp-rtc) (8)
- [GRP_TEMPERATURE](#grp-temperature) (4)
- [GRP_FAN](#grp-fan) (5)


## GRP_SYSTEM

| Mnemonic | Reply | Name | Dims | Range | Access |
|---|---|---|---|---|---|
| `?` | `DEV` | DEV | — | 256…288 | read-only |
| `@` | `ADBG` | DBG_ADDR | — | 0…4294967295 | read/write |
| `>` | `DDBG` | DBG_DATA | — | 0…4294967295 | read/write |
| `+` |  | DBG_SETBIT | — | 0…4294967295 | read/write |
| `-` |  | DBG_RESETBIT | — | 0…4294967295 | read/write |
| `SYdai` |  | DBG_DATA_IDX | `[1,1048577]` | 0…4294967295 | read/write |
| `SYori` |  | DBG_OR_IDX | `[1,1048577]` | 0…4294967295 | read/write |
| `SYani` |  | DBG_AND_IDX | `[1,1048577]` | 0…4294967295 | read/write |
| `SYpri` |  | DBG_EN_PRIVATE | `[1]` | 0…1 | read/write |
| `&` |  | ERROR | `[1]` | 0…4294967295 | read-only |
| `$` |  | DOLLAR | `[1]` | 0…4294967295 | read-only |
| `#` |  | DIESE | — | 0…3 | read/write |
| `SYpig` |  | PING | — | 0…4294967295 | read/write |
| `*` |  | READY | — | 0…1 | read-only |

## GRP_LAN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `ITlen` | LAN_ENABLE | — | 0…1 | read/write |
| `ITlrs` | LAN_RESET | — | 0…1 | read/write |
| `ITlst` | LAN_STORE | — | 0…1 | read/write |
| `ITlip` | LAN_IP | `[3,4]` | 0…255 | read/write |
| `ITlpo` | LAN_PORT | `[3]` | 0…65535 | read/write |
| `ITlnk` | LAN_NETMASK | — | 0…24 | read/write |
| `ITlpr` | LAN_PROTOCOL | — | 0…1 | read/write |
| `ITmac` | LAN_MAC_ADDRESS | `[6]` | 0…255 | read-only |

## GRP_CONTROL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `CTfar` | FACTORY_RESET | — | 0…1 | read/write |
| `CTfrp` | FACTORY_RESET_PROGRESS | — | 0…100 | read-only |
| `CTmrs` | POS_MEMORY_RESET | — | 0…1 | read/write |
| `CTpmr` | PRESET_MEMORY_RESET | `[8]` | 0…1 | read/write |
| `CTupd` | UPDATER | — | 0…4294967295 | read/write |
| `CTsto` | CSTORE | — | 0…1 | read-only |
| `CTloc` | LOCK | — | 0…2 | read/write |
| `CTbri` | LCD_BRIGHTNESS | — | 1…8 | read/write |
| `CTkbr` | KEY_BRIGHTNESS | — | 10…100 | read/write |
| `CTaxi` | AXION | — | 0…1 | read/write |
| `CTaut` | AUTO_LOCK | — | 0…1 | read/write |
| `CTatk` | AUTO_TAKE | `[2]` | 0…1 | read/write |
| `CTmir` | MATRIX_MIRROR | `[8]` | 0…3 | read/write |
| `CTstb` | AUTO_STEPBACK | `[2]` | 0…1 | read/write |
| `CTpmu` | PRESET_UPDATE_MODE | — | 0…1 | read/write |
| `CTpmf` | PRESET_MGMT_MATRIX_FAV | — | 0…3 | read/write |
| `CTfrm` | FREEZE_MODE | — | 0…1 | read/write |
| `CTket` | PROG_KEY_ET | `[6]` | 0…6 | read/write |
| `CTktw` | PROG_KEY_TW | `[6]` | 0…10 | read/write |
| `CTked` | PROG_KEY_ED | `[6]` | 0…255 | read/write |
| `CTqfr` | QUICK_FRAME_SEL | `[2]` | 0…7 | read/write |
| `CTqfa` | QUICK_FRAME | `[2]` | 0…1 | read/write |
| `CTqfl` | QUICK_FRAME_ALL | — | 0…1 | read/write |
| `CTaqf` | AUTO_QUICK_FRAME | — | 0…1 | read/write |
| `CTbfi` | BLACK_FILL | — | 0…1 | read/write |
| `CTdid` | DISABLE_ID | — | 0…1 | read/write |
| `CThul` | HIDE_UNUSED_LAYERS | — | 0…1 | read/write |
| `CTrsr` | RS232_RATE | — | 0…5 | read/write |
| `CTreb` | REBOOT_DEVICE | — | 0…1 | read/write |
| `CTiip` | IMPORT_INHIB_PROCESS | — | 0…1 | read/write |
| `CTpcr` | PIP_COLOR_RED | — | 0…255 | read/write |
| `CTpcg` | PIP_COLOR_GREEN | — | 0…255 | read/write |
| `CTpcb` | PIP_COLOR_BLUE | — | 0…255 | read/write |
| `CTvom` | VIDEO_OUT_CFGMODE | — | 0…2 | read/write |

## GRP_DEVICE_FLAGS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `DFmix` | FLAG_MIXER_MODE_AVAILABLE | — | 0…1 | read-only |
| `DFmat` | FLAG_MATRIX_MODE_AVAILABLE | — | 0…1 | read-only |
| `DFqua` | FLAG_QUADRAVISION_MODE_AVAILABLE | — | 0…1 | read-only |
| `DFseb` | FLAG_ESEB_MODE_AVAILABLE | — | 0…1 | read-only |
| `DFmeb` | FLAG_MULTI_ESEB_MODE_AVAILABLE | — | 0…1 | read-only |
| `DFmmt` | FLAG_MATRIX_MODE_TYPE | — | 0…2 | read-only |
| `DFmos` | FLAG_MOSAIC_DISPLAY_AVAILABLE | — | 0…1 | read-only |
| `DFosd` | FLAG_OSD_AVAILABLE | — | 0…1 | read-only |
| `DFvdo` | FLAG_VIDEO_OUT_AVAILABLE | — | 0…1 | read-only |
| `DFlay` | FLAG_LAYER_AVAILABLE | `[4,8]` | 0…1 | read-only |
| `DFflp` | FLAG_LAYER_FLIP_AVAILABLE | — | 0…1 | read-only |
| `DFsiz` | FLAG_BACKGROUND_IS_RESIZEABLE | — | 0…1 | read-only |
| `DFtra` | FLAG_TRANSITION_AVAILABLE | `[7,8]` | 0…1 | read-only |
| `DFbda` | FLAG_BORDER_STYLE_AVAILABLE | `[5]` | 0…1 | read-only |
| `DFfro` | FLAG_FRAMES_ONLY | — | 0…1 | read-only |
| `DFvso` | FLAG_VIDEO_OUT_SDI_PLUG_ONLY | — | 0…1 | read-only |
| `DFmvo` | FLAG_VIDEO_OUT_MODE_RECORDING | — | 0…1 | read-only |
| `DFmoa` | FLAG_VIDEO_OUT_MODE_OUT1 | — | 0…1 | read-only |
| `DFmob` | FLAG_VIDEO_OUT_MODE_OUT2 | — | 0…1 | read-only |

## GRP_DEVICE_INFO

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `DIcid` | CARD_ID | `[10]` | 0…4294967295 | read-only |
| `DIcrv` | CARD_REV | `[10]` | 0…255 | read-only |
| `DIcip` | CARD_IS_PLUG | `[10]` | 0…1 | read-only |
| `DIcma` | CARD_MANDATORY | `[10]` | 0…1 | read-only |
| `DIcop` | CARD_OPTION | `[10]` | 0…4294967295 | read-only |
| `DIcce` | CARD_CONFIG_ERROR | — | 0…1 | read-only |
| `DIdsn` | DEVICE_SERIAL_NUM | — | 0…4294967295 | read-only |
| `DIdre` | DEVICE_REF | — | 0…4294967295 | read-only |
| `DIddc` | DEVICE_DATECODE | — | 0…4294967295 | read-only |
| `DIdst` | DEVICE_STRING | `[4]` | 0…255 | read-only |

## GRP_STANDBY

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SBsta` | STDBY_STATUS | — | 0…1 | read-only |
| `SBreq` | STDBY_REQUEST | — | 0…1 | read/write |
| `SBprg` | STDBY_PROGRESS | — | 0…100 | read-only |
| `SBpon` | STDBY_PROJ_ON | `[50]` | 0…255 | read/write |
| `SBpof` | STDBY_PROJ_OFF | `[50]` | 0…255 | read/write |
| `SBpra` | STDBY_PROJ_RATE | — | 0…5 | read/write |
| `SBpct` | STDBY_PROJ_CTRL | — | 0…4 | read/write |

## GRP_VERSION

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `VEvar` | VER_VAR | — | 0…65535 | read-only |
| `VEupd` | VER_UPDATER | — | 0…4294967295 | read-only |
| `VEfga` | VER_FPGA | `[1,3]` | 0…4294967295 | read-only |
| `VEfts` | VER_FPGA_TIMESTAMP | `[1,3]` | 0…4294967295 | read-only |
| `VEmic` | VER_MICRO | `[1]` | 0…4294967295 | read-only |

## GRP_INPUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INava` | IN_AVAILABLE | `[10]` | 0…1 | read-only |
| `INfrz` | IN_FREEZE | `[10]` | 0…1 | read/write |
| `INbla` | IN_BLACK | `[10]` | 0…1 | read/write |
| `INcsg` | IN_CURRENT_SYNCHRO_GROUP | `[10]` | 0…1 | read-only |
| `INplg` | IN_PLUG | `[10]` | 0…4 | read/write |
| `INpav` | IN_PLUG_AVAILABLE | `[10,5]` | 0…1 | read-only |
| `INsrc` | IN_SOURCE | `[10,5]` | 0…999 | read/write |
| `INtyp` | IN_TYPE | `[10,5]` | 0…13 | read/write |
| `INsyl` | IN_SYNC_LOAD | `[10,5]` | 0…1 | read/write |
| `INuse` | IN_USED | `[10,5]` | 0…1 | read/write |
| `INsdd` | IN_SD_STD | `[10,5]` | 0…7 | read/write |
| `INsds` | IN_SD_STA | `[10,5]` | 0…1 | read/write |
| `INscf` | IN_SD_3D_COMB_FILTER | `[10,5]` | 0…3 | read/write |
| `INsgr` | IN_PLUG_SYNCHRO_GROUP | `[10,5]` | 0…1 | read/write |
| `INhdc` | IN_HDCP_ENABLE | `[10,5]` | 0…1 | read/write |
| `INlre` | IN_HDBT_LONG_REACH_ENABLE | `[10,5]` | 0…1 | read/write |
| `INhqm` | IN_HDBT_SIG_QUALITY_MIN | `[10,5]` | 0…255 | read-only |
| `INhqn` | IN_HDBT_SIG_QUALITY_MAX | `[10,5]` | 0…255 | read-only |
| `INhqr` | IN_HDBT_SIG_QUALITY_REFRESH | — | 0…1 | read/write |
| `INcbp` | IN_PLUG_CAN_BE_POE | `[10,5]` | 0…1 | read-only |

## GRP_INPUT_AUTOSET

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INasa` | IN_AUTOSET_ALL | — | 0…1 | read/write |
| `INaap` | IN_AUTOSET_ALL_PROGRESS | — | 0…100 | read-only |
| `INasi` | IN_AUTOSET_INPUT | `[10]` | 0…1 | read/write |
| `INapi` | IN_AUTOSET_INPUT_PROGRESS | `[10]` | 0…100 | read-only |
| `INasp` | IN_AUTOSET_PLUG | `[10,5]` | 0…1 | read/write |
| `INapp` | IN_AUTOSET_PLUG_PROGRESS | `[10,5]` | 0…100 | read-only |

## GRP_INPUT_AUTOCENTER

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INain` | IN_AUTOCENTER_INPUT | `[10]` | 0…2 | read/write |
| `INaip` | IN_AUTOCENTER_INPUT_PROGRESS | `[10]` | 0…100 | read-only |

## GRP_INPUT_KEYING

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `INkge` | IN_KEYING_GRAB_ENABLE | — | 0…1 | read/write |
| `INkgi` | IN_KEYING_GRAB_INPUT | — | 0…9 | read/write |
| `INkgp` | IN_KEYING_GRAB_PLUG | — | 0…4 | read/write |
| `INkgo` | IN_KEYING_GRAB_OUTPUT | — | 0…1 | read/write |
| `INkgt` | IN_KEYING_GRAB_GET | — | 0…1 | read/write |
| `INgrh` | IN_KEYING_GRAB_H | — | 0…65535 | read/write |
| `INgrv` | IN_KEYING_GRAB_V | — | 0…65535 | read/write |

## GRP_INPUT_SIGNALS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `ISscc` | SIG_SCAN_COMPLETE | `[10,5]` | 0…1 | read-only |
| `ISspr` | SIG_SCAN_PRESENT | `[10,5]` | 0…1 | read-only |
| `ISsva` | SIG_SCAN_VALID | `[10,5]` | 0…1 | read-only |
| `ISdfo` | SIG_DETECTED_FORMAT | `[10,5]` | 0…56 | read-only |
| `IScfo` | SIG_CURRENT_FORMAT | `[10,5]` | 0…56 | read-only |
| `IScfn` | SIG_CURRENT_FORMAT_NAME | `[10,5,16]` | 0…255 | read-only |
| `ISlfo` | SIG_LIST_FORMAT | `[10,5,8]` | 0…255 | read-only |
| `ISswi` | SIG_SIGNAL_WIDTH | `[10,5]` | 0…65535 | read-only |
| `ISshe` | SIG_SIGNAL_HEIGHT | `[10,5]` | 0…65535 | read-only |
| `ISfwi` | SIG_FORMAT_WIDTH | `[10,5]` | 0…65535 | read-only |
| `ISfhe` | SIG_FORMAT_HEIGHT | `[10,5]` | 0…65535 | read-only |
| `ISiwi` | SIG_IMAGE_WIDTH | `[10,5]` | 0…65535 | read-only |
| `ISihe` | SIG_IMAGE_HEIGHT | `[10,5]` | 0…65535 | read-only |
| `ISfok` | SIG_FORMAT_KIND | `[10,5]` | 0…3 | read-only |
| `IShdc` | SIG_HDCP | `[10,5]` | 0…1 | read-only |
| `ISsnu` | SIG_SLOTNUMBER | `[10,5]` | 0…512 | read-only |
| `ISffi` | SIG_FREQ_FIELD | `[10,5]` | 0…4294967295 | read-only |
| `ISfli` | SIG_FREQ_LINE | `[10,5]` | 0…4294967295 | read-only |
| `IShpo` | SIG_HPOL | `[10,5]` | 0…1 | read-only |
| `ISvpo` | SIG_VPOL | `[10,5]` | 0…1 | read-only |
| `ISvss` | SIG_VSYNC_SIZE | `[10,5]` | 0…65535 | read-only |
| `IShss` | SIG_HSYNC_SIZE | `[10,5]` | 0…65535 | read-only |
| `ISsyt` | SIG_SYNC_TYPE | `[10,5]` | 0…3 | read-only |
| `ISsct` | SIG_SCANTYPE | `[10,5]` | 0…3 | read-only |
| `IShtt` | SIG_HTOTAL_THEORIC | `[10,5]` | 0…65535 | read-only |
| `IShtm` | SIG_HTOTALMAX | `[10,5]` | 0…65535 | read-only |
| `ISrcf` | SIG_REPEAT_COEFF | `[10,5]` | 1…10 | read-only |
| `IShvi` | SIG_HAS_AVI | `[10,5]` | 0…1 | read-only |
| `IScdh` | SIG_COLOR_DEPTH | `[10,5]` | 0…4 | read-only |
| `IScsp` | SIG_COLOR_SPACE | `[10,5]` | 0…10 | read-only |
| `ISthd` | SIG_STEREO_3D_STATUS | `[10,5]` | 0…10 | read-only |
| `ISaud` | SIG_AUDIO_DETECTED | `[10,5]` | 0…1 | read-only |
| `ISaus` | SIG_AUDIO_SUPPORTED | `[10,5]` | 0…1 | read-only |
| `ISaut` | SIG_AUDIO_TYPE | `[10,5]` | 0…17 | read-only |
| `ISacc` | SIG_AUDIO_CHANNEL_COUNT | `[10,5]` | 0…8 | read-only |
| `ISasf` | SIG_AUDIO_SAMPLING_FREQ | `[10,5]` | 0…4294967295 | read-only |
| `ISacy` | SIG_AUDIO_HAS_COPYRIGHT | `[10,5]` | 0…1 | read-only |
| `ISpas` | SIG_POE_IS_ACTIVE | `[10,5]` | 0…1 | read-only |
| `ISpoc` | SIG_POE_OVERCURRENT | `[10,5]` | 0…1 | read-only |

## GRP_INPUT_SETTINGS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `IEdef` | SET_DEFAULT | `[10,5]` | 0…1 | read/write |
| `IEufo` | SET_USER_FORMAT | `[10,5]` | 0…56 | read/write |
| `IEbhp` | SET_BLK_HPOS | `[10,5]` | 0…511 | read/write |
| `IEbvp` | SET_BLK_VPOS | `[10,5]` | 0…511 | read/write |
| `IEbhs` | SET_BLK_HSIZE | `[10,5]` | 0…511 | read/write |
| `IEbvs` | SET_BLK_VSIZE | `[10,5]` | 0…511 | read/write |
| `IEbri` | SET_BRIGHTNESS | `[10,5]` | 0…255 | read/write |
| `IEcon` | SET_CONTRAST | `[10,5]` | 0…255 | read/write |
| `IEclr` | SET_COLOR | `[10,5]` | 0…255 | read/write |
| `IEhue` | SET_HUE | `[10,5]` | 0…360 | read/write |
| `IEhto` | SET_HTOTAL_OFFSET | `[10,5]` | 0…511 | read/write |
| `IEpha` | SET_PHASE | `[10,5]` | 0…63 | read/write |
| `IEugr` | SET_USER_GAIN_R | `[10,5]` | 0…255 | read/write |
| `IEugg` | SET_USER_GAIN_G | `[10,5]` | 0…255 | read/write |
| `IEugb` | SET_USER_GAIN_B | `[10,5]` | 0…255 | read/write |
| `IEpdb` | SET_PULLDOWN_2_2 | `[10,5]` | 0…1 | read/write |
| `IEpdc` | SET_PULLDOWN_3_2 | `[10,5]` | 0…1 | read/write |
| `IEdll` | SET_DEINT_LOW_LATENCY | `[10,5]` | 0…1 | read/write |
| `IEudo` | SET_UNDEROVER | `[10,5]` | 0…1 | read/write |
| `IEain` | SET_ASPECT_IN | `[10,5]` | 0…6 | read/write |
| `IEaou` | SET_ASPECT_OUT | `[10,5]` | 0…3 | read/write |
| `IEpcr` | SET_CROP_PREDEF | `[10,5]` | 0…4 | read/write |
| `IEchs` | SET_CROP_LEFT | `[10,5]` | 0…4095 | read/write |
| `IEcvs` | SET_CROP_TOP | `[10,5]` | 0…4095 | read/write |
| `IEche` | SET_CROP_RIGHT | `[10,5]` | 0…4095 | read/write |
| `IEcve` | SET_CROP_BOTTOM | `[10,5]` | 0…4095 | read/write |
| `IEsha` | SET_SHARPNESS | `[10,5]` | 0…2 | read/write |
| `IEkty` | SET_KEYING_TYPE | `[10,5]` | 0…4 | read/write |
| `IEkrl` | SET_KEYING_R_LEVEL | `[10,5]` | 0…255 | read/write |
| `IEkgl` | SET_KEYING_G_LEVEL | `[10,5]` | 0…255 | read/write |
| `IEkbl` | SET_KEYING_B_LEVEL | `[10,5]` | 0…255 | read/write |
| `IEkto` | SET_KEYING_TOLER | `[10,5]` | 0…255 | read/write |
| `IEklw` | SET_KEYING_LUMA_LOW_LEVEL | `[10,5]` | 0…255 | read/write |
| `IEkhl` | SET_KEYING_LUMA_HIGH_LEVEL | `[10,5]` | 0…255 | read/write |
| `IEkda` | SET_KEYING_DSK_ALPHA | `[10,5]` | 0…255 | read/write |
| `IEkin` | SET_KEYING_INVERT | `[10,5]` | 0…1 | read/write |

## GRP_INPUT_SETTINGS_MEMORIES

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SMgin` | SETMEM_GLOBAL_INHIB | — | 0…1 | read/write |
| `SMids` | SETMEM_ID_SOURCE | `[65]` | 0…256 | read/write |
| `SMidt` | SETMEM_ID_TYPE | `[65]` | 0…13 | read/write |
| `SMidf` | SETMEM_ID_FREQ_FIELD | `[65]` | 0…4294967295 | read/write |
| `SMidl` | SETMEM_ID_FREQ_LINE | `[65]` | 0…4294967295 | read/write |
| `SMsyt` | SETMEM_ID_SYNC_TYPE | `[65]` | 0…3 | read/write |
| `SMidv` | SETMEM_ID_VSYNC_SIZE | `[65]` | 0…65535 | read/write |
| `SMidh` | SETMEM_ID_HSYNC_SIZE | `[65]` | 0…65535 | read/write |
| `SMida` | SETMEM_ID_VPOL | `[65]` | 0…1 | read/write |
| `SMidb` | SETMEM_ID_HPOL | `[65]` | 0…1 | read/write |
| `SMici` | SETMEM_ID_CREATOR_INPUT | `[65]` | 0…9 | read/write |
| `SMicp` | SETMEM_ID_CREATOR_PLUG | `[65]` | 0…4 | read/write |
| `SMufo` | SETMEM_USER_FORMAT | `[65]` | 0…56 | read/write |
| `SMhpo` | SETMEM_BLK_HPOS | `[65]` | 0…511 | read/write |
| `SMvpo` | SETMEM_BLK_VPOS | `[65]` | 0…511 | read/write |
| `SMhsi` | SETMEM_BLK_HSIZE | `[65]` | 0…511 | read/write |
| `SMvsi` | SETMEM_BLK_VSIZE | `[65]` | 0…511 | read/write |
| `SMbri` | SETMEM_BRIGHTNESS | `[65]` | 0…255 | read/write |
| `SMcon` | SETMEM_CONTRAST | `[65]` | 0…255 | read/write |
| `SMclr` | SETMEM_COLOR | `[65]` | 0…255 | read/write |
| `SMhue` | SETMEM_HUE | `[65]` | 0…360 | read/write |
| `SMhto` | SETMEM_HTOTAL_OFFSET | `[65]` | 0…511 | read/write |
| `SMpha` | SETMEM_PHASE | `[65]` | 0…63 | read/write |
| `SMugr` | SETMEM_USER_GAIN_R | `[65]` | 0…255 | read/write |
| `SMugg` | SETMEM_USER_GAIN_G | `[65]` | 0…255 | read/write |
| `SMugb` | SETMEM_USER_GAIN_B | `[65]` | 0…255 | read/write |
| `SMpdb` | SETMEM_PULLDOWN_2_2 | `[65]` | 0…1 | read/write |
| `SMpdc` | SETMEM_PULLDOWN_3_2 | `[65]` | 0…1 | read/write |
| `SMdll` | SETMEM_DEINT_LOW_LATENCY | `[65]` | 0…1 | read/write |
| `SMudo` | SETMEM_UNDEROVER | `[65]` | 0…1 | read/write |
| `SMain` | SETMEM_ASPECT_IN | `[65]` | 0…6 | read/write |
| `SMaou` | SETMEM_ASPECT_OUT | `[65]` | 0…3 | read/write |
| `SMpcr` | SETMEM_CROP_PREDEF | `[65]` | 0…4 | read/write |
| `SMchs` | SETMEM_CROP_LEFT | `[65]` | 0…4095 | read/write |
| `SMcvs` | SETMEM_CROP_TOP | `[65]` | 0…4095 | read/write |
| `SMche` | SETMEM_CROP_RIGHT | `[65]` | 0…4095 | read/write |
| `SMcve` | SETMEM_CROP_BOTTOM | `[65]` | 0…4095 | read/write |
| `SMsha` | SETMEM_SHARPNESS | `[65]` | 0…2 | read/write |
| `SMkty` | SETMEM_KEYING_TYPE | `[65]` | 0…4 | read/write |
| `SMkrl` | SETMEM_KEYING_R_LEVEL | `[65]` | 0…255 | read/write |
| `SMkgl` | SETMEM_KEYING_G_LEVEL | `[65]` | 0…255 | read/write |
| `SMkbl` | SETMEM_KEYING_B_LEVEL | `[65]` | 0…255 | read/write |
| `SMkto` | SETMEM_KEYING_TOLER | `[65]` | 0…255 | read/write |
| `SMklw` | SETMEM_KEYING_LUMA_LOW_LEVEL | `[65]` | 0…255 | read/write |
| `SMkhl` | SETMEM_KEYING_LUMA_HIGH_LEVEL | `[65]` | 0…255 | read/write |
| `SMkda` | SETMEM_KEYING_DSK_ALPHA | `[65]` | 0…255 | read/write |
| `SMkin` | SETMEM_KEYING_INVERT | `[65]` | 0…1 | read/write |
| `SMage` | SETMEM_AGE_COUNTER | `[65]` | 0…4294967295 | read/write |
| `SMalu` | SETMEM_AGE_LAST_USED | `[65]` | 0…4294967295 | read/write |
| `SMval` | SETMEM_IS_VALID | `[65]` | 0…1 | read/write |
| `SMupd` | SETMEM_UPDATE | `[65]` | 0…1 | read/write |

## GRP_PRESET_ID

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PIpid` | PI_PRESET_ID | `[2,3]` | 0…255 | read/write |
| `PIwur` | PI_WAS_UNMODIFIED_REQUEST | `[2,3]` | 1…1 | read/write |
| `PIwus` | PI_WAS_UNMODIFIED_STATUS | `[2,3]` | 0…1 | read-only |

## GRP_PRESET_ELEMENT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PRinp` | PE_INPUTNUM | `[2,3,8]` | 0…11 | read/write |
| `PRsmm` | PE_SMOOTH_MOVE | `[2,3,8]` | 0…1 | read/write |
| `PRfli` | PE_FLIP | `[2,3,8]` | 0…3 | read/write |
| `PRftr` | PE_FORCE_TRANSITION | `[2,3,8]` | 0…1 | read/write |
| `PRpoh` | PE_POS_H | `[2,3,8]` | 0…65535 | read/write |
| `PRpov` | PE_POS_V | `[2,3,8]` | 0…65535 | read/write |
| `PRsih` | PE_SIZE_H | `[2,3,8]` | 0…65535 | read/write |
| `PRsiv` | PE_SIZE_V | `[2,3,8]` | 0…65535 | read/write |
| `PRcph` | PE_CROP_WIN_POS_H | `[2,3,8]` | 0…65535 | read/write |
| `PRcpv` | PE_CROP_WIN_POS_V | `[2,3,8]` | 0…65535 | read/write |
| `PRcsh` | PE_CROP_WIN_SIZE_H | `[2,3,8]` | 0…58981 | read/write |
| `PRcsv` | PE_CROP_WIN_SIZE_V | `[2,3,8]` | 0…58981 | read/write |
| `PRalp` | PE_ALPHA | `[2,3,8]` | 0…255 | read/write |
| `PRbst` | PE_BORDER_STYLE | `[2,3,8]` | 0…4 | read/write |
| `PRbcr` | PE_BORDER_COLOR_RED | `[2,3,8]` | 0…255 | read/write |
| `PRbcg` | PE_BORDER_COLOR_GREEN | `[2,3,8]` | 0…255 | read/write |
| `PRbcb` | PE_BORDER_COLOR_BLUE | `[2,3,8]` | 0…255 | read/write |
| `PRbal` | PE_BORDER_ALPHA | `[2,3,8]` | 0…255 | read/write |
| `PRbsh` | PE_BORDER_SIZE_H | `[2,3,8]` | 0…127 | read/write |
| `PRbsv` | PE_BORDER_SIZE_V | `[2,3,8]` | 0…127 | read/write |
| `PRshp` | PE_BORDER_SHADOW_POS | `[2,3,8]` | 0…3 | read/write |
| `PRotr` | PE_OPENING_TRANSITION | `[2,3,8]` | 0…6 | read/write |
| `PRowa` | PE_OPENING_TRANSITION_WAY | `[2,3,8]` | 0…10 | read/write |
| `PRodu` | PE_OPENING_DURATION | `[2,3,8]` | 0…255 | read/write |
| `PRctr` | PE_CLOSING_TRANSITION | `[2,3,8]` | 0…6 | read/write |
| `PRcwa` | PE_CLOSING_TRANSITION_WAY | `[2,3,8]` | 0…10 | read/write |
| `PRcdu` | PE_CLOSING_DURATION | `[2,3,8]` | 0…255 | read/write |

## GRP_PRESET_UPDATE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PUscu` | PU_SCREEN_UPDATE | `[2]` | 1…1 | read/write |

## GRP_PRESET_MEMORY

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PMinp` | PM_INPUTNUM | `[8,2,8]` | 0…10 | read/write |
| `PMsmm` | PM_SMOOTH_MOVE | `[8,2,8]` | 0…1 | read/write |
| `PMfli` | PM_FLIP | `[8,2,8]` | 0…3 | read/write |
| `PMftr` | PM_FORCE_TRANSITION | `[8,2,8]` | 0…1 | read/write |
| `PMpoh` | PM_POS_H | `[8,2,8]` | 0…65535 | read/write |
| `PMpov` | PM_POS_V | `[8,2,8]` | 0…65535 | read/write |
| `PMsih` | PM_SIZE_H | `[8,2,8]` | 0…65535 | read/write |
| `PMsiv` | PM_SIZE_V | `[8,2,8]` | 0…65535 | read/write |
| `PMcph` | PM_CROP_WIN_POS_H | `[8,2,8]` | 0…65535 | read/write |
| `PMcpv` | PM_CROP_WIN_POS_V | `[8,2,8]` | 0…65535 | read/write |
| `PMcsh` | PM_CROP_WIN_SIZE_H | `[8,2,8]` | 0…58981 | read/write |
| `PMcsv` | PM_CROP_WIN_SIZE_V | `[8,2,8]` | 0…58981 | read/write |
| `PMalp` | PM_ALPHA | `[8,2,8]` | 0…255 | read/write |
| `PMbst` | PM_BORDER_STYLE | `[8,2,8]` | 0…4 | read/write |
| `PMbcr` | PM_BORDER_COLOR_RED | `[8,2,8]` | 0…255 | read/write |
| `PMbcg` | PM_BORDER_COLOR_GREEN | `[8,2,8]` | 0…255 | read/write |
| `PMbcb` | PM_BORDER_COLOR_BLUE | `[8,2,8]` | 0…255 | read/write |
| `PMbal` | PM_BORDER_ALPHA | `[8,2,8]` | 0…255 | read/write |
| `PMbsh` | PM_BORDER_SIZE_H | `[8,2,8]` | 0…127 | read/write |
| `PMbsv` | PM_BORDER_SIZE_V | `[8,2,8]` | 0…127 | read/write |
| `PMshp` | PM_BORDER_SHADOW_POS | `[8,2,8]` | 0…3 | read/write |
| `PMotr` | PM_OPENING_TRANSITION | `[8,2,8]` | 0…6 | read/write |
| `PMowa` | PM_OPENING_TRANSITION_WAY | `[8,2,8]` | 0…10 | read/write |
| `PModu` | PM_OPENING_DURATION | `[8,2,8]` | 0…255 | read/write |
| `PMctr` | PM_CLOSING_TRANSITION | `[8,2,8]` | 0…6 | read/write |
| `PMcwa` | PM_CLOSING_TRANSITION_WAY | `[8,2,8]` | 0…10 | read/write |
| `PMcdu` | PM_CLOSING_DURATION | `[8,2,8]` | 0…255 | read/write |
| `PMssh` | PM_SCREEN_STATUS_SIZE_H | `[8,2]` | 0…65536 | read/write |
| `PMssv` | PM_SCREEN_STATUS_SIZE_V | `[8,2]` | 0…65536 | read/write |
| `PMsml` | PM_SCREEN_MAX_LAYERS | `[8,2]` | 0…4 | read/write |
| `PMpst` | PM_WAS_SETTED | `[8]` | 0…1 | read/write |

## GRP_TAKE_CONTROL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `GCtak` | TAKE | `[2]` | 0…1 | read/write |
| `GCtal` | TAKE_ALL | — | 0…1 | read/write |
| `GCtav` | TAKEAVA | `[2]` | 0…1 | read-only |
| `GCtio` | TAKEINFO | `[2]` | 0…2 | read-only |
| `GCtba` | TBAR | `[2]` | 0…10000 | read/write |

## GRP_PRESET_CONTROL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `GCsba` | STEPBACK | `[2]` | 0…1 | read/write |
| `GCrpr` | RELOAD_PROGRAM | `[2]` | 0…1 | read/write |
| `GCfrl` | FREEZE_LAYER | `[2,8]` | 0…1 | read/write |
| `GCfsc` | FREEZE_SCREEN | `[2]` | 0…1 | read/write |
| `GCfra` | FREEZE_ALL | — | 0…1 | read/write |
| `GCsrq` | PRESET_SAVE_REQUEST | `[3,8]` | 0…1 | read/write |
| `GClrq` | PRESET_LOAD_REQUEST | `[2,8,2,2,12]` | 0…1 | read/write |
| `GCply` | PREVIEWED_LAYER | — | 0…6 | read/write |
| `GCmdi` | MOSAIC_DISPLAY | — | 0…1 | read/write |
| `GCqly` | SET_LAYOUT | `[2,3]` | 0…26 | read/write |

## GRP_OUTPUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUava` | OUT_AVAILABLE | `[2]` | 0…1 | read-only |
| `OUena` | OUT_ENABLE | `[2]` | 0…1 | read-only |
| `OUpat` | OUT_PATTERN | `[2]` | 0…9 | read/write |
| `OUpct` | OUT_PATTERN_CENTERING | `[2]` | 0…1 | read/write |
| `OUhdc` | OUT_HDCP_ENABLE | `[2]` | 0…1 | read/write |
| `OUlre` | OUT_HDBT_LONG_REACH_ENABLE | `[2]` | 0…1 | read/write |
| `OUfdm` | OUT_FORCE_DVI_MODE | `[2]` | 0…1 | read/write |
| `OUpoh` | OUT_POS | `[2]` | 1…8 | read/write |

## GRP_OUTPUT_FORMAT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUsou` | OUT_SYNC_OUTPUT | — | 0…1 | read/write |
| `OUfor` | OUT_FORMAT | `[2]` | 0…45 | read/write |
| `OUrmo` | OUT_RATE_MODE | `[2]` | 0…1 | read/write |
| `OUfru` | OUT_FORMAT_UPDATE | `[2]` | 0…1 | read/write |

## GRP_OUTPUT_VALIDITY

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUfva` | OUT_FORMAT_VALIDITY | `[2,46]` | 0…1 | read-only |
| `OUrva` | OUT_RATE_VALIDITY | `[2,46,3]` | 0…255 | read-only |

## GRP_OUTPUT_MASTER

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUrat` | OUT_MASTER_RATE | `[2]` | 0…15 | read/write |

## GRP_OUTPUT_FRAMELOCK

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUfrm` | OUT_FRAMELOCK_MODE | `[2]` | 0…2 | read/write |
| `OUfrf` | OUT_FRAMELOCK_REF | `[2]` | 0…10 | read/write |
| `OUfrv` | OUT_FRAMELOCK_REF_AVAILABLE | `[2,11]` | 0…1 | read-only |
| `OUfes` | OUT_FRAMELOCK_REF_STATUS | `[2]` | 0…10 | read-only |
| `OUfrs` | OUT_FRAMELOCK_STATUS | `[2]` | 0…6 | read-only |

## GRP_OUTPUT_SIGTYPE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUsav` | OUT_SIGTYPE_ANALOG_VALIDITY | `[2,4]` | 0…1 | read-only |
| `OUsia` | OUT_SIGTYPE_ANALOG | `[2]` | 0…3 | read/write |
| `OUsas` | OUT_SIGTYPE_ANALOG_STATUS | `[2]` | 0…3 | read-only |
| `OUsid` | OUT_SIGTYPE_DIGITAL | `[2]` | 0…3 | read/write |
| `OUsds` | OUT_SIGTYPE_DIGITAL_STATUS | `[2]` | 1…3 | read-only |

## GRP_OUTPUT_STATUS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUfvs` | OUT_FORMAT_VALID_STATUS | `[2]` | 0…1 | read-only |
| `OUfst` | OUT_FORMAT_STATUS | `[2]` | 0…45 | read-only |
| `OUrms` | OUT_RATE_MODE_STATUS | `[2]` | 0…1 | read-only |
| `OUrst` | OUT_RATE_STATUS | `[2]` | 0…125000 | read-only |
| `OUkin` | OUT_KIND_STATUS | `[2]` | 2…3 | read-only |
| `OUshs` | OUT_SIZE_H_STATUS | `[2]` | 0…65535 | read-only |
| `OUsvs` | OUT_SIZE_V_STATUS | `[2]` | 0…65535 | read-only |
| `OUhwa` | OUT_HDCP_WARNING | `[2]` | 0…1 | read-only |
| `OUcsg` | OUT_CURRENT_SYNC_GROUP | `[2]` | 0…1 | read-only |

## GRP_OUTPUT_PLUG_STATUS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OUpls` | OUT_PLUG_STATUS | `[2,8]` | 0…3 | read-only |
| `OUihc` | OUT_PLUG_ISHDCP | `[2,8]` | 0…1 | read-only |
| `OUpmd` | OUT_PLUG_MONITOR_DETECTED | `[2,8]` | 0…1 | read-only |
| `OUpmn` | OUT_PLUG_MONITOR_NAME | `[2,8,16]` | 0…255 | read-only |
| `OUphm` | OUT_PLUG_IS_IN_HDMI_MODE | `[2,8]` | 0…1 | read-only |

## GRP_CUSTOM_COMPUTE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `CCcht` | CUSTOM_COMP_CVT_HUTIL | — | 20…256 | read/write |
| `CCcvt` | CUSTOM_COMP_CVT_VUTIL | — | 120…1200 | read/write |
| `CCcra` | CUSTOM_COMP_CVT_RATE | — | 50000…120000 | read/write |
| `CCrdb` | CUSTOM_COMP_CVT_REDUCED_BLK | — | 0…1 | read/write |
| `CCfhs` | CUSTOM_COMP_FULL_HSYNC | — | 32…500 | read/write |
| `CChpo` | CUSTOM_COMP_FULL_HSYNC_POL | — | 0…1 | read/write |
| `CChbp` | CUSTOM_COMP_FULL_HBACKPORCH | — | 32…1000 | read/write |
| `CChfp` | CUSTOM_COMP_FULL_HFRONTPORCH | — | 8…3000 | read/write |
| `CCfht` | CUSTOM_COMP_FULL_HUTIL | — | 160…2048 | read/write |
| `CCvsy` | CUSTOM_COMP_FULL_VSYNC | — | 2…20 | read/write |
| `CCvpo` | CUSTOM_COMP_FULL_VSYNC_POL | — | 0…1 | read/write |
| `CCvbp` | CUSTOM_COMP_FULL_VBACKPORCH | — | 4…150 | read/write |
| `CCvfp` | CUSTOM_COMP_FULL_VFRONTPORCH | — | 1…50 | read/write |
| `CCvua` | CUSTOM_COMP_FULL_VUTIL | — | 120…1200 | read/write |
| `CCfra` | CUSTOM_COMP_FULL_RATE | — | 22000…120000 | read/write |
| `CChto` | CUSTOM_COMP_HTOTAL_STATUS | — | 0…65535 | read-only |
| `CCvto` | CUSTOM_COMP_VTOTAL_STATUS | — | 0…65535 | read-only |
| `CCpfs` | CUSTOM_COMP_PIXEL_FREQ_STATUS | — | 0…4294967295 | read-only |
| `CClfs` | CUSTOM_COMP_LINE_FREQ_STATUS | — | 0…4294967295 | read-only |
| `CCscv` | CUSTOM_COMP_SELECT_CVT | — | 0…1 | read/write |
| `CCnam` | CUSTOM_COMP_NAME | `[32]` | 0…255 | read/write |
| `CCcrq` | CUSTOM_COMP_CHECK_REQUEST | — | 0…1 | read/write |
| `CCcst` | CUSTOM_COMP_CHECK_STATUS | — | 0…5 | read/write |
| `CCsfo` | CUSTOM_COMP_SAVE_FORMAT | `[11]` | 0…1 | read/write |

## GRP_CUSTOM_FORMAT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OCnam` | CUSTOM_FORMAT_NAME | `[11,32]` | 0…255 | read/write |
| `OCrdb` | CUSTOM_FORMAT_REDUCED_BLK | `[11]` | 0…1 | read/write |
| `OCfhs` | CUSTOM_FORMAT_HSYNC | `[11]` | 32…500 | read/write |
| `OChpo` | CUSTOM_FORMAT_HSYNC_POL | `[11]` | 0…1 | read/write |
| `OChbp` | CUSTOM_FORMAT_HBACKPORCH | `[11]` | 32…1000 | read/write |
| `OChfp` | CUSTOM_FORMAT_HFRONTPORCH | `[11]` | 8…1000 | read/write |
| `OCfht` | CUSTOM_FORMAT_HUTIL | `[11]` | 160…4096 | read/write |
| `OChto` | CUSTOM_FORMAT_HTOTAL | `[11]` | 0…65535 | read/write |
| `OCvsy` | CUSTOM_FORMAT_VSYNC | `[11]` | 2…50 | read/write |
| `OCvpo` | CUSTOM_FORMAT_VSYNC_POL | `[11]` | 0…1 | read/write |
| `OCvbp` | CUSTOM_FORMAT_VBACKPORCH | `[11]` | 4…200 | read/write |
| `OCvfp` | CUSTOM_FORMAT_VFRONTPORCH | `[11]` | 1…200 | read/write |
| `OCvua` | CUSTOM_FORMAT_VUTIL | `[11]` | 120…2160 | read/write |
| `OCvto` | CUSTOM_FORMAT_VTOTAL | `[11]` | 0…65535 | read/write |
| `OCfra` | CUSTOM_FORMAT_RATE | `[11]` | 22000…120000 | read/write |
| `OCwst` | CUSTOM_FORMAT_WAS_SETTED | `[11]` | 0…1 | read/write |
| `OCdel` | CUSTOM_FORMAT_DELETE | `[11]` | 0…1 | read/write |

## GRP_OUTPUT_CONTROL

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OCfli` | OUT_FLICK | `[2]` | 0…7 | read/write |
| `OCgam` | OUT_GAMMA | `[2]` | 5…40 | read/write |

## GRP_VIDEO_OUT_FORMAT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `VOfor` | VIDOUT_FORMAT | — | 0…13 | read/write |
| `VOrat` | VIDOUT_RATE | — | 0…9 | read/write |
| `VOfru` | VIDOUT_FORMAT_UPDATE | — | 0…1 | read/write |

## GRP_VIDEO_OUT_VALIDITY

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `VOrva` | VIDOUT_RATE_VALIDITY | `[14,3]` | 0…255 | read-only |

## GRP_VIDEO_OUT_STATUS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `VOfvs` | VIDOUT_FORMAT_VALID_STATUS | — | 0…1 | read-only |
| `VOfst` | VIDOUT_FORMAT_STATUS | — | 0…13 | read-only |
| `VOrst` | VIDOUT_RATE_STATUS | — | 0…125000 | read-only |
| `VOkin` | VIDOUT_KIND_STATUS | — | 0…2 | read-only |
| `VOshs` | VIDOUT_SIZE_H_STATUS | — | 0…65535 | read-only |
| `VOsvs` | VIDOUT_SIZE_V_STATUS | — | 0…65535 | read-only |
| `VOpls` | VIDOUT_PLUG_ACTIVE_STATUS | `[3]` | 0…2 | read-only |
| `VOhwa` | VIDOUT_HDCP_WARNING | — | 0…1 | read-only |

## GRP_VIDEO_OUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `VOmod` | VIDOUT_MODE | — | 0…3 | read/write |
| `VOpoh` | VIDOUT_IMAGE_POS_H | — | 0…65535 | read/write |
| `VOpov` | VIDOUT_IMAGE_POS_V | — | 0…65535 | read/write |
| `VOsih` | VIDOUT_IMAGE_SIZE_H | — | 0…65535 | read/write |
| `VOsiv` | VIDOUT_IMAGE_SIZE_V | — | 0…65535 | read/write |
| `VOpat` | VIDOUT_PATTERN | — | 0…9 | read/write |
| `VOpct` | VIDOUT_PATTERN_CENTERING | — | 0…1 | read/write |
| `VObcr` | VIDOUT_BACK_COLOR_R | — | 0…255 | read/write |
| `VObcg` | VIDOUT_BACK_COLOR_G | — | 0…255 | read/write |
| `VObcb` | VIDOUT_BACK_COLOR_B | — | 0…255 | read/write |
| `VOfli` | VIDOUT_FLICK | — | 0…7 | read/write |
| `VOgam` | VIDOUT_GAMMA | — | 5…40 | read/write |
| `VOsha` | VIDOUT_SHARPNESS | — | 0…255 | read/write |
| `VOovc` | VIDOUT_OVERSCAN_COMPENSATION | — | 0…1 | read/write |

## GRP_SCREEN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SCbre` | OSCREEN_BACK_COLOR_R | `[2]` | 0…255 | read/write |
| `SCbgr` | OSCREEN_BACK_COLOR_G | `[2]` | 0…255 | read/write |
| `SCbbl` | OSCREEN_BACK_COLOR_B | `[2]` | 0…255 | read/write |
| `SCsih` | OSCREEN_SIZE_H | `[2]` | 1…8 | read/write |
| `SCsiv` | OSCREEN_SIZE_V | `[2]` | 1…8 | read/write |
| `SCssh` | OSCREEN_STATUS_SIZE_H | `[2]` | 0…65536 | read-only |
| `SCssv` | OSCREEN_STATUS_SIZE_V | `[2]` | 0…65536 | read-only |
| `SCmly` | OSCREEN_MAX_LAYERS | `[2]` | 0…4 | read-only |

## GRP_SCREEN_CONFIG

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SGswm` | SCREEN_CFG_SWITCHER_MODE | — | 0…3 | read/write |
| `SGsam` | SCREEN_CFG_SWITCHER_AUDIO_MODE | — | 0…2 | read/write |
| `SGsou` | SCREEN_CFG_OUT | `[2]` | 0…1 | read-only |
| `SGomo` | SCREEN_CFG_OUT_MODE | `[2]` | 0…2 | read-only |
| `SGors` | SCREEN_CFG_OUT_RESOURCES | `[2]` | 0…4 | read-only |

## GRP_SOFTEDGE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `SEmod` | SOFTEDGE_MODE | — | 0…1 | read/write |
| `SEcov` | SOFTEDGE_COVERING_SIZE | — | 0…1023 | read/write |
| `SEcen` | SOFTEDGE_CURVE_ENABLE | — | 0…1 | read/write |
| `SEpoi` | SOFTEDGE_POINT | `[2,2,2]` | 462…817 | read/write |
| `SEbof` | SOFTEDGE_BLACK_AREA_OFFSET | `[2,2]` | 0…127 | read/write |
| `SEbrl` | SOFTEDGE_BLACK_R_LEVEL | `[2]` | 0…127 | read/write |
| `SEblg` | SOFTEDGE_BLACK_G_LEVEL | `[2]` | 0…127 | read/write |
| `SEbbl` | SOFTEDGE_BLACK_B_LEVEL | `[2]` | 0…127 | read/write |
| `SEupm` | SOFTEDGE_UNIFIED_PREVIEW_MODE | — | 0…1 | read/write |

## GRP_EDID_IN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `EIava` | EDID_IN_AVAILABLE | `[10,5]` | 0…1 | read-only |
| `EIdat` | EDID_IN_DATA | `[10,5,256]` | 0…255 | read/write |
| `EIstr` | EDID_IN_STORE | `[10,5]` | 0…1 | read/write |
| `EIohc` | EDID_IN_ORIGIN_HASHCODE | `[10,5]` | 0…4294967295 | read/write |
| `EIhcd` | EDID_IN_HASHCODE | `[10,5]` | 0…4294967295 | read-only |
| `EIpfa` | EDID_IN_PREF_FORMAT_AVAILABLE | `[10,5,16]` | 0…255 | read-only |
| `EIspf` | EDID_IN_SET_PREF_FORMAT | `[10,5]` | 0…120 | read/write |
| `EIpfn` | EDID_IN_PREF_FORMAT_NAME | `[10,5,16]` | 0…255 | read-only |

## GRP_EDID_OUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `EOava` | EDID_OUT_AVALAIBLE | `[2,8]` | 0…1 | read-only |
| `EOdat` | EDID_OUT_DATA | `[2,8,256]` | 0…255 | read-only |
| `EOval` | EDID_OUT_VALIDITY | `[2,8]` | 0…1 | read-only |
| `EOred` | EDID_OUT_READ | `[2,8]` | 0…1 | read/write |
| `EOhcd` | EDID_OUT_HASHCODE | `[2,8]` | 0…4294967295 | read-only |

## GRP_AUDIO_INPUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `AUmod` | AUDIO_MODE | `[2]` | 0…1 | read/write |
| `AUipm` | AUDIO_INPUT_PLUG_MAP | `[10,5]` | 0…7 | read/write |
| `AUaia` | AUDIO_INPUT_AVAILABLE | `[25]` | 0…1 | read-only |
| `AUile` | AUDIO_INPUT_LEVEL | `[25]` | 0…255 | read/write |
| `AUiba` | AUDIO_INPUT_BALANCE | `[25]` | 0…90 | read/write |
| `AUiim` | AUDIO_INPUT_IS_MONO | `[25]` | 0…1 | read/write |
| `AUimu` | AUDIO_INPUT_MUTE | `[25]` | 0…1 | read/write |
| `AUial` | AUDIO_INPUT_ANALOG_LEVEL | `[5]` | 0…34 | read/write |
| `AUiac` | AUDIO_INPUT_ANALOG_IS_CLIPPING | `[5]` | 0…1 | read-only |
| `AUsgr` | AUDIO_INPUT_SDI_GROUP_SELECT | `[17]` | 0…3 | read/write |
| `AUisl` | AUDIO_INPUT_SDI_CHANNEL_LEFT | `[17]` | 0…3 | read/write |
| `AUisr` | AUDIO_INPUT_SDI_CHANNEL_RIGHT | `[17]` | 0…3 | read/write |
| `AUgst` | AUDIO_INPUT_SDI_GROUP_STATUS | `[17,4]` | 0…1 | read-only |
| `AUssr` | AUDIO_INPUT_SPDIF_SAMPLING_RATE | `[25]` | 0…4294967295 | read-only |

## GRP_AUDIO_OUTPUT

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `AUomv` | AUDIO_OUTPUT_MASTER_VOLUME | `[2]` | 0…192 | read/write |
| `AUoba` | AUDIO_OUTPUT_BALANCE | `[2]` | 0…90 | read/write |
| `AUomu` | AUDIO_OUTPUT_MUTE | `[2]` | 0…1 | read/write |
| `AUoim` | AUDIO_OUTPUT_IS_MONO | `[2]` | 0…1 | read/write |
| `AUoad` | AUDIO_OUTPUT_AUTO_DELAY | `[2]` | 0…1 | read/write |
| `AUode` | AUDIO_OUTPUT_DELAY | `[2]` | 0…80 | read/write |
| `AUoal` | AUDIO_OUTPUT_ANALOG_LEVEL | `[2]` | 0…15 | read/write |
| `AUoss` | AUDIO_OUTPUT_SPDIF_STANDARD | — | 0…1 | read/write |
| `AUoci` | AUDIO_OUTPUT_CURRENT_INPUT | `[2]` | 0…24 | read-only |
| `AUfin` | AUDIO_FORCE_INPUT | — | 0…4 | read/write |
| `AUodi` | AUDIO_OUTPUT_DESEMB_INPUT | `[2]` | 0…10 | read/write |
| `AUmdi` | AUDIO_OUTPUT_MUTE_EMBEDDED | `[2]` | 0…1 | read/write |
| `AUosc` | AUDIO_OUTPUT_OSC_ENABLE | `[2]` | 0…1 | read/write |

## GRP_AUDIO_LEVELS

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `AUorl` | AUDIO_OUTPUT_RAW_LEVEL | — | 0…4294967295 | read-only |
| `AUore` | AUDIO_OUTPUT_RAW_ENABLE | — | 0…1 | read/write |

## GRP_STILL_PIX

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PSmod` | STILL_MODE | — | 0…5 | read/write |
| `PSidx` | STILL_INDEX | — | 0…15 | read/write |
| `PSexe` | STILL_EXECUTE | — | 0…1 | read/write |
| `PSabt` | STILL_ABORT | — | 0…1 | read/write |
| `PSprg` | STILL_PROGRESS | — | 0…100 | read-only |
| `PSsta` | STILL_STATUS | — | 0…5 | read-only |
| `PSfrv` | STILL_FRAME_VALID | `[8]` | 0…1 | read-only |
| `PSlov` | STILL_LOGO_VALID | `[16]` | 0…1 | read-only |
| `PSfsh` | STILL_FRAME_SIZE_H | `[8]` | 0…32367 | read-only |
| `PSfsv` | STILL_FRAME_SIZE_V | `[8]` | 0…32367 | read-only |
| `PSlsh` | STILL_LOGO_SIZE_H | `[16]` | 0…32367 | read-only |
| `PSlsv` | STILL_LOGO_SIZE_V | `[16]` | 0…32367 | read-only |
| `PSlic` | STILL_LOGO_ANIM_IMAGE_COUNT | — | 0…255 | read-only |
| `PSlrf` | STILL_LOGO_ANIM_REFRESH | — | 0…100 | read-only |

## GRP_STILL_PIX_CAPTURE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `PCorg` | CAPTURE_ORIGIN | — | 0…1 | read/write |
| `PCpoh` | CAPTURE_POS_H | — | 32768…65535 | read/write |
| `PCpov` | CAPTURE_POS_V | — | 32768…65535 | read/write |
| `PCsih` | CAPTURE_SIZE_H | — | 1…32767 | read/write |
| `PCsiv` | CAPTURE_SIZE_V | — | 1…32767 | read/write |
| `PCkty` | CAPTURE_KEYING_TYPE | — | 0…2 | read/write |
| `PCklr` | CAPTURE_KEYING_LEVEL_R | — | 0…255 | read/write |
| `PCklb` | CAPTURE_KEYING_LEVEL_B | — | 0…255 | read/write |
| `PCklg` | CAPTURE_KEYING_LEVEL_G | — | 0…255 | read/write |
| `PCkto` | CAPTURE_KEYING_TOLER | — | 0…255 | read/write |
| `PCklw` | CAPTURE_KEYING_LUMA_LOW_LEVEL | — | 0…255 | read/write |
| `PCkhl` | CAPTURE_KEYING_LUMA_HIGH_LEVEL | — | 0…255 | read/write |
| `PCkin` | CAPTURE_KEYING_INVERT | — | 0…1 | read/write |
| `PCkge` | CAPTURE_KEYING_GRAB_ENABLE | — | 0…1 | read/write |
| `PCkgt` | CAPTURE_KEYING_GRAB_GET | — | 0…1 | read/write |
| `PCkgh` | CAPTURE_KEYING_GRAB_H | — | 0…65535 | read/write |
| `PCkgv` | CAPTURE_KEYING_GRAB_V | — | 0…65535 | read/write |
| `PCkbc` | CAPTURE_KEYING_BACK_COLOR | — | 0…7 | read/write |
| `PCtim` | CAPTURE_TIME | — | 1…100 | read/write |
| `PClmi` | CAPTURE_LOGO_ANIM_MAX_IMAGE | — | 1…255 | read/write |
| `PClic` | CAPTURE_LOGO_ANIM_IMAGE_COUNT | — | 1…255 | read/write |
| `PClrf` | CAPTURE_LOGO_ANIM_REFRESH | — | 1…100 | read/write |

## GRP_OSD

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `OSden` | OSD_ENABLE | — | 0…1 | read/write |
| `OSddf` | OSD_DISPLAYED_FIELD | — | 0…127 | read/write |

## GRP_RTC

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `RTval` | RTC_TIME_IS_VALID | — | 0…1 | read-only |
| `RTsec` | RTC_SECONDS | — | 0…59 | read/write |
| `RTmin` | RTC_MINUTES | — | 0…59 | read/write |
| `RThou` | RTC_HOURS | — | 0…23 | read/write |
| `RTday` | RTC_DAY | — | 1…31 | read/write |
| `RTmon` | RTC_MONTH | — | 0…11 | read/write |
| `RTyea` | RTC_YEAR | — | 2000…2199 | read/write |
| `RTreq` | RTC_REQUESTS | — | 0…2 | read/write |

## GRP_TEMPERATURE

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `TEcar` | TEMP_MONITOR | `[6]` | 0…65535 | read-only |
| `TEcal` | TEMP_MONITOR_ALARM | `[6]` | 0…2 | read-only |
| `TEref` | TEMP_REFRESH | — | 0…1 | read/write |
| `TEdal` | TEMP_DEVICE_ALARM | — | 0…2 | read-only |

## GRP_FAN

| Mnemonic | Name | Dims | Range | Access |
|---|---|---|---|---|
| `FAfga` | FAN_SPEED_FPGA | `[1,3]` | 0…65535 | read-only |
| `FAfal` | FAN_SPEED_FPGA_ALARM | `[1,3]` | 0…1 | read-only |
| `FAcas` | FAN_SPEED_CASE | `[3]` | 0…65535 | read-only |
| `FAcal` | FAN_SPEED_CASE_ALARM | `[3]` | 0…1 | read-only |
| `FAref` | FAN_REFRESH | — | 0…1 | read/write |
