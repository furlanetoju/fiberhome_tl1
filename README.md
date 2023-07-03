<img src=fiberhome-1-01.png>

# Documentação FiberHome

<h1>TL1</h1>

**Tudo que estiver dentro de chaves {} é variável e as chaves não pertencem ao comando.**

**Login TL1** (Usuário e senha do UNM)
```
LOGIN:::CTAG::UN={usuário},PWD={senha};
```
**Listar onus não autorizadas**
```
LST-UNREGONU::OLTID={IP_OLT}:CTAG::;
```
**Autorizar ONU/ONT VIA TL1**
```
ADD-ONU::OLTID={IP_OLT},PONID=NA-NA-{SLOT}-{PON}:CTAG::AUTHTYPE=MAC,ONUID={MAC},NAME={NOME DA ONU},ONUTYPE={MODELO},BANDTYPE=1G/1G;
```
Exemplo:
```
ADD-ONU::OLTID=10.111.4.2,PONID=NA-NA-15-16:CTAG::AUTHTYPE=MAC,ONUID=FHTT96a5dc70,NAME=TESTE_ONU_BRIDGE,ONUTYPE=AN5506-04-FA,BANDTYPE=1G/1G;
```
**Deletar ONU**
```
DEL-ONU::OLTID={IP_OLT},PONID=NA-NA-{SLOT}-{PON}:CTAG::ONUIDTYPE=MAC,ONUID={MAC};
```
**ESCREVER O ALIAS-NAME E O NOME DA ONU**
```
CFG-ONUNAMEANDDESC::OLTID={IP_OLT},PONID=NA-NA-{SLOT}-{PON},ONUIDTYPE=MAC,ONUID={MAC}:CTAG::ONUNAME={NOME DA ONU},ONUDESC={DESCRIÇÃO DO ALIASNAME};
```
