# Bando — releases

Este repositório não tem código. Ele carrega os **instaladores** do Bando e o
`latest.json` que uma cópia instalada lê para se atualizar sozinha.

O código-fonte é privado. O que é público é a distribuição: os arquivos que você
baixa e a assinatura que prova que são eles mesmos.

## Baixar

A versão mais recente fica em **[Releases](../../releases/latest)**.

| Sistema | Arquivo |
| --- | --- |
| macOS (Apple Silicon) | `.dmg` |
| Windows | `-setup.exe` |
| Linux | `.AppImage`, `.deb` ou `.rpm` |

**O primeiro instalador ainda não é assinado pelo sistema operacional.** O
macOS vai avisar que o desenvolvedor não foi verificado (botão direito › Abrir,
uma vez) e o Windows vai mostrar o SmartScreen (Mais informações › Executar
assim mesmo). Isso é sobre o *primeiro* install; a assinatura que o atualizador
confere é outra, e essa já existe.

## Como a atualização funciona

O Bando pergunta a este repositório, uma vez a cada vez que abre, se saiu versão
nova. Quando sai, ele avisa num aviso com um botão e **espera você dizer que
sim** — nunca troca o aplicativo por baixo de alguém que está no meio de uma
transação aberta contra um banco de produção.

O pacote baixado é conferido com [minisign](https://jedisct1.github.io/minisign/)
contra uma chave pública compilada dentro do aplicativo. Um feed adulterado não
instala nada: a assinatura é verificada antes do primeiro byte ser gravado.

A checagem automática pode ser desligada em Configurações, e o botão de
*Procurar atualizações* continua lá.

Duas exceções que vale saber antes de escolher o arquivo:

- **`.deb` e `.rpm` não se atualizam sozinhos.** O atualizador não substitui um
  pacote que ele não instalou — quem quer atualização automática no Linux usa o
  `.AppImage`.
- **Mac Intel ainda não tem build.** O release traz macOS para Apple Silicon.

## Problemas

Abra uma [issue](../../issues). Se o aviso do Bando te deu um identificador de
erro — algo como `syntax_error-a1b2c3` — cole ele junto: é por ele que o
problema é localizado, e ele não carrega nada do seu banco.
