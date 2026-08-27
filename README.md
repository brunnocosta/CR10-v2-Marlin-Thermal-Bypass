# CR-10 V2 - Firmware Marlin com bypass de sensores de temperatura

Este repositório contém uma build personalizada do Marlin 2.1.2.8 para uma CR-10 V2 com adaptação de hardware para contornar sensores de temperatura danificados ou com entradas queimadas.

## Objetivo do projeto

O foco principal desta customização foi manter a impressora funcionando mesmo quando os sensores de temperatura do hotend e/ou da mesa apresentavam falhas elétricas ou entradas comprometidas. A solução foi ajustar o mapeamento dos pinos do firmware para utilizar entradas alternativas e manter a lógica de controle da máquina operando de forma estável.

## Visão geral

- Base: Marlin 2.1.2.8
- Placa: `BOARD_RAMPS_CREALITY`
- Máquina: `CR-10 V2`
- Drivers: TMC2208 standalone em X, Y, Z e E0
- Hotend sensor pin remapped para `TEMP_0_PIN = 11 (A11)`
- Bed sensor pin remapped para `TEMP_BED_PIN = 15 (E2)`
- Bootscreen e status screen customizados ativos como parte da personalização visual

## Alterações principais

- Ajuste do mapeamento de temperatura para contornar entradas queimadas.
- Personalização do firmware para a CR-10 V2 com RAMPS/Creality.
- Atualização do `pins_RAMPS.h` para refletir os pinos alternativos em uso.
- Manutenção da base oficial do Marlin, com adaptações locais do hardware.

## Arquivos de configuração relevantes

- `Marlin/Configuration.h` — configuração ativa do firmware e opções da máquina
- `Marlin/Configuration_adv.h` — ajustes avançados do Marlin
- `Marlin/_Bootscreen.h` — bitmap do bootscreen customizado
- `Marlin/_Statusscreen.h` — bitmap do status screen customizado
- `Marlin/src/pins/ramps/pins_RAMPS.h` — mapeamento dos pinos da RAMPS, incluindo sensor temp
- `config/README.md` — lembrete do local das configurações originais do upstream

## Configuração atual destacada

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

Este repositório representa uma solução prática para manter uma impressora CR-10 V2 operando com entradas de temperatura comprometidas. A base upstream continua sendo o Marlin oficial, mas a configuração local foi adaptada para a realidade do hardware e ao problema de bypass dos sensores.

## Licença

Este projeto mantém a licença GPL do Marlin original. Consulte o arquivo [LICENSE](LICENSE) para detalhes.
