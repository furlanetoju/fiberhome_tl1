<img src=fiberhome-1-01.png>

# Documentação FiberHome

<h1>TL1</h1>

**Tudo que estiver dentro de chaves {} é variável e as chaves não pertencem ao comando.**

Lembrando que o **TL1 do Unm2000**, roda na porta **3337**. Conectamos via **telnet** no endereço **IP do unm2000** na porta **3337** e todo comando termina com **;**
```
telnet {IP_do_Unm2000} 3337
```
Depois que fazermos a conexão acima, podemos ver uma saída parecida com essa:

<img src=Captura\de\tela\de\2023-07-03\11-56-54.png>

**Login TL1** (Usuário e senha do UNM)
```
LOGIN:::CTAG::UN={usuário},PWD={senha};
```
**Exemplo de login:**

<img src=Captura de tela de 2023-07-03 11-57-53.png>

**Listar onus não autorizadas**
```
LST-UNREGONU::OLTID={IP_OLT}:CTAG::;
```
**Autorizar ONU/ONT VIA TL1**
```
ADD-ONU::OLTID={IP_OLT},PONID=NA-NA-{SLOT}-{PON}:CTAG::AUTHTYPE=MAC,ONUID={MAC},NAME={NOME DA ONU},ONUTYPE={MODELO DA ONU},BANDTYPE=1G/1G;
```
Exemplo:
```
ADD-ONU::OLTID=10.111.4.2,PONID=NA-NA-15-16:CTAG::AUTHTYPE=MAC,ONUID=FHTT96a5dc70,NAME=TESTE_ONU_BRIDGE,ONUTYPE={MODELO DA ONU},BANDTYPE=1G/1G;
```
**Deletar ONU**
```
DEL-ONU::OLTID={IP_OLT},PONID=NA-NA-{SLOT}-{PON}:CTAG::ONUIDTYPE=MAC,ONUID={MAC};
```
**ESCREVER O ALIAS-NAME E O NOME DA ONU**
```
CFG-ONUNAMEANDDESC::OLTID={IP_OLT},PONID=NA-NA-{SLOT}-{PON},ONUIDTYPE=MAC,ONUID={MAC}:CTAG::ONUNAME={NOME DA ONU},ONUDESC={DESCRIÇÃO DO ALIASNAME};
```
**PEGA O NOME DA ONU, VERSÃO, SLOT, PON E NUMERO DA ONU**
```
QUERY-ONUINFO::OLTID={IP_OLT},PONID=NA-NA-{SLOT}-{PON},ONUIDTYPE=MAC,ONUID={MAC}:CTAG::;
```
**ADD A ONU JÁ COM O ALIAS NAME**
```
ADD-ONU::OLTID={IP_OLT},PONID=NA-NA-{SLOT}-{PON}:CTAG::AUTHTYPE=MAC,ONUID={MAC},NAME={NOME DA ONU},DESC={DESCRIÇÃO DO ALIASNAME},ONUTYPE={MODEL},BANDTYPE=1G/1G;
```
**PEGA A VELOCIDADE DA PORTA LAN**
```
LST-ONULANINFO::OLTID={IP_OLT},PONID=NA-NA-{SLOT}-{PON},ONUIDTYPE=MAC,ONUID={MAC},ONUPORT=NA-NA-NA-1:CTAG::;
```
