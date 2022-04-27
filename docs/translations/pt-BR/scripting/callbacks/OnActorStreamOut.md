---
title: OnActorStreamOut
description: Essa callback é executada quando um determinado Actor sai do campo de visão do jogador (cliente).
tags: []
---

<VersionWarn name='callback' version='SA-MP 0.3.7' />

## Descrição

Essa callback é executada quando um determinado Actor sai do campo de visão do jogador (cliente).

| Nome        | Descrição                                                      |
| ----------- | -------------------------------------------------------------- |
| actorid     | ID do Actor que está sendo saindo do campo de visão do jogador.|
| forplayerid | ID do jogador no qual se baseia o campo de visão.              |

## Retorno

Sempre a primeira a ser declarada em filterscripts.

## Exemplos

```c
public OnActorStreamOut(actorid, forplayerid)
{
    new string[40];
    format(string, sizeof(string), "O Actor %d saiu do seu campo de visão.", actorid);
    SendClientMessage(forplayerid, 0xFFFFFFFF, string);
    return 1;
}
```

## Notas

<TipNPCCallbacks />