# Aplicativo Android para Controle de Fechaduras via ESP8266

Este repositório contém o código-fonte de um aplicativo Android desenvolvido em Kotlin, utilizado para controlar fechaduras eletrônicas baseadas no microcontrolador ESP8266. O sistema oferece controle via rede local, utilizando pacotes UDP para comunicação entre o aplicativo e a placa.

## Visão Geral

Cada fechadura é controlada por uma placa ESP8266 conectada a um módulo NFC PN532. O primeiro smartphone a se conectar à fechadura torna-se o **administrador** da mesma. Apenas o administrador tem permissão para adicionar novos usuários ou cartões RFID ao sistema.

O sistema permite:

- Abrir a fechadura via aplicativo
- Abrir a fechadura com cartões RFID
- Adicionar e remover usuários autorizados
- Adicionar e remover cartões RFID válidos
- Alterar configurações da fechadura (somente para administradores)

## Funcionalidades

### Conexão com a Fechadura

- A comunicação entre o aplicativo e o ESP8266 é feita via UDP.
- A fechadura é descoberta na rede local através de um processo de broadcast.

### Gerenciamento de Usuários

- O primeiro usuário a se conectar à fechadura se torna o **administrador**.
- O administrador pode autorizar múltiplos smartphones a controlarem a fechadura.
- Usuários autorizados podem apenas abrir a fechadura, sem permissões administrativas.

### Cartões RFID

- O módulo NFC PN532 permite o uso de cartões RFID para abertura da fechadura.
- Somente o administrador pode adicionar ou remover RFIDs válidos.
- O processo de cadastro de um cartão é iniciado via aplicativo e concluído ao aproximar o cartão da fechadura.

## Implementação

- O aplicativo é construído em Kotlin, utilizando bibliotecas nativas do Android.
- A comunicação UDP é gerenciada em segundo plano para garantir responsividade e estabilidade da interface.
- A interface do aplicativo permite interação simples e rápida com múltiplas fechaduras na mesma rede.

## Código da Placa ESP8266

- O firmware da placa foi desenvolvido em linguagem C.
- O ESP8266 gerencia localmente os usuários, RFIDs e permissões.
- A placa escuta pacotes UDP e responde com confirmações de operação.
- O módulo NFC PN532 é utilizado para leitura dos cartões RFID e envio de notificações ao aplicativo, quando necessário.

## Observações
- O sistema foi projetado para ambientes locais e não requer servidores externos.
- Caso o administrador perca o acesso, será necessário reinicializar fisicamente a placa ESP8266 para redefinir o controle administrativo.

