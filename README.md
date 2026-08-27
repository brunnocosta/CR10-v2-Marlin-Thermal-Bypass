# CR-10 V2 - Firmware Marlin customizado

Este repositório contém uma build personalizada do Marlin 2.1.2.8 para uma impressora CR-10 V2 com configuração adaptada para hardware RAMPS/Creality e personalizações visuais no bootscreen e status screen.

## Visão geral

- Base: Marlin 2.1.2.8
- Placa: `BOARD_RAMPS_CREALITY`
- Máquina: `CR-10 V2`
- Drivers: TMC2208 standalone em X, Y, Z e E0
- Bootscreen e status screen customizados ativos
- Sensor de temperatura do hotend ajustado para `TEMP_0_PIN = 11`
- Sensor de temperatura da mesa ajustado para `TEMP_BED_PIN = 15`



## Arquivos de configuração relevantes

- `Marlin/Configuration.h` — configuração ativa do firmware e opções da máquina
- `Marlin/Configuration_adv.h` — ajustes avançados do Marlin
- `Marlin/_Bootscreen.h` — bitmap do bootscreen customizado
- `Marlin/_Statusscreen.h` — bitmap do status screen customizado
- `Marlin/src/pins/ramps/pins_RAMPS.h` — mapeamento dos pinos da RAMPS
- `config/README.md` — lembrete do local das configurações originais do upstream

## Configuração atual destacada

A configuração principal foi ajustada para este hardware específico:

- `CUSTOM_MACHINE_NAME "CR-10 V2"`
- `MOTHERBOARD BOARD_RAMPS_CREALITY`
- `SHOW_BOOTSCREEN` ativado
- `SHOW_CUSTOM_BOOTSCREEN` ativado
- `CUSTOM_STATUS_SCREEN_IMAGE` ativado
- `TEMP_0_PIN` definido como `11` em `pins_RAMPS.h`
- `TEMP_BED_PIN` definido como `15` em `pins_RAMPS.h`

## Build e upload

Os comandos usados neste workspace para compilar e gravar o firmware são:

```bash
platformio run
platformio run --target upload
```

O ambiente já foi validado localmente com build e upload concluídos com sucesso.

## Observações

Este repositório é uma adaptação específica do projeto original do Marlin. A base upstream continua sendo a stack oficial do Marlin, mas a configuração local foi personalizada para a máquina e para a experiência visual do usuário.

## Licença

Este projeto mantém a licença GPL do Marlin original. Consulte o arquivo [LICENSE](LICENSE) para detalhes.
