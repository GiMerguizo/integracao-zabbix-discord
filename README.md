# Integracao Zabbix + Discord
Repositório com o passo-a-passo para criar uma integração que envia alertas do Zabbix para um canal do Discord.

## Configuração do Discord
1. Criar um novo servidor, caso ainda não tenha
2. Criar um novo canal de texto ou utilizar um já existente
3. Ir em "Editar canal" na engrenagem ao lado do nome do canal
4. Navegar em Integrações > Webhooks > Novo webhook <br>
    4.1 Configurar o nome do Bot e conferir se está no canal correto <br>
    4.2 Copiar URL do Webhook, conforme a imagem abaixo <br>
![image](https://github.com/user-attachments/assets/5564a7d0-a209-4b63-bb39-f3ab2f77066b) <br>
    4.3 Guardar o endereço copiado em algum editor de texto <br>

## Configuração do Zabbix
_Atenção: O zabbix já está instalado na versão 6.0LTS_ <br>
1. Baixar o arquivo **media_discord.yaml**
2. Navegar em Administration > Media types > Import
3. Importar o arquivo baixado <br>
![image](https://github.com/user-attachments/assets/cb668bee-c24f-4d00-abe6-228f47645771)
4. Navegar em Administration > General > Macros
   - Adicionar a macro **{$ZABBIX.URL}** e configurar conforme o seu enderço ip/dns <br>
![image](https://github.com/user-attachments/assets/f422a403-5982-4b27-a00d-a99fe7383c63)
4. Navegar em Configuration > Actions > Trigger Actions <br>
![image](https://github.com/user-attachments/assets/0ba8c3aa-ffe6-4179-b323-b058367b7a75)
5. Configurar Action <br>
![image](https://github.com/user-attachments/assets/cc440cf0-2c2e-4cc9-836b-c92e6aa25e00)
6. Configurar Operation <br>
![image](https://github.com/user-attachments/assets/861af259-92ad-478f-8dc6-3376c9a6032d) <br>
![image](https://github.com/user-attachments/assets/72b1719d-b3cc-4590-a6f1-4835e8b307ac)
7. Conferir se ficou parecido com isso: <br>
![image](https://github.com/user-attachments/assets/d930191a-cc7b-481b-8918-0efa0c4c8dbb)

## Teste
Muito bom! Agora você já tem a sua integração configurada. <br>
Para validar, utilizei um host de teste que estava sendo monitorado e parei o seu zabbix-agent (`systemctl stop zabbix-agent`). <br>
Aguardei 3 minutos e o alerta apareceu no Zabbix e foi enviado para o canal configurado do Discord.

![image](https://github.com/user-attachments/assets/e81aa08d-2e92-468d-9532-bf6839e7fc28)


## Referências
🔗 [Documentação Oficial](https://www.zabbix.com/br/integrations/discord) <br>
📹 [Vídeo de como enviar alertas do Zabbix para o Discord](https://youtu.be/eIjRDiV3RhI?si=G8i9EoQRXujUsWou) <br>
