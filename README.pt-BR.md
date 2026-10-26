# SecretDNS

**Ferramenta gratuita para Windows que contorna a vigilância da Internet (DPI) com DNS over HTTPS e fragmentação SNI, ativada com um único clique.**

[English](README.md) · [한국어](README.ko.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [Español](README.es.md) · Português (Brasil) · [Français](README.fr.md)

> Este documento é uma tradução. Em caso de divergência, a [versão em coreano](README.ko.md) prevalece.

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%2F%2011-0078D4)
![License](https://img.shields.io/badge/license-Freeware-brightgreen)
[![Download](https://img.shields.io/badge/download-kilho.net-orange)](https://down.kilho.net/secretdns?lang=pt)

![Tela do SecretDNS](images/secretdns-en.png)

## Visão geral

Ao abrir um site, o computador envia duas coisas em texto puro: uma **consulta DNS** pedindo o endereço IP do site e o **nome do site (SNI)**, que vai no primeiro pacote de toda conexão HTTPS. Os equipamentos de inspeção (DPI) das operadoras ou administradores de rede leem os dois para saber qual site você está visitando e, se quiserem, cortam a conexão ou redirecionam para uma página de aviso.

O SecretDNS fecha as duas brechas com um único toque no **botão de cadeado**.

- **DNS** — Trata as consultas DNS do computador com **criptografia (DoH)** por meio de um servidor como o Cloudflare. As configurações de rede do Windows não são tocadas; por isso, ao parar o programa tudo volta ao normal na hora, e se o computador desligar de repente durante a execução, ao reiniciar a Internet funciona como sempre, sem deixar rastro.
- **SNI** — **Impede que o nome do site fique exposto aos equipamentos de inspeção** nas conexões HTTPS. A conexão com o site funciona normalmente e, como só a parte do nome é tratada, quase não há perda de velocidade.

Sites que param de funcionar quando fragmentados (bancos, meios de pagamento) passam intactos graças a uma **lista de exceções** integrada, e o **Relatório** mostra como cada site foi tratado. Para sites que o desvio de DNS não consegue abrir — como o **erro 451**, comum em países sem liberdade na Internet, em que o próprio site recusa conexões vindas daquele país — o **proxy misto** faz só esses sites passarem por outro país. Apenas os domínios que você indicar passam por lá, então o resto da sua Internet mantém a velocidade total.

O SecretDNS não é uma VPN. Ele não esconde seu endereço IP nem criptografa todo o tráfego: trata apenas os dois pontos usados para vigilância, DNS e SNI.

## Principais recursos

- **Um clique** — Basta pressionar o **botão de cadeado** na tela inicial. Um clique no ícone da bandeja ou no cadeado no canto superior direito de Configurações também liga e desliga.
- **DNS over HTTPS** — Cloudflare por padrão. Adicione seus próprios servidores e marque vários; o SecretDNS alterna entre eles automaticamente. Há também o modo **Servidores**, que usa um servidor DNS sem criptografia (ex.: 1.1.1.1).
- **Sem alterar as configurações do Windows** — As configurações DNS do adaptador de rede não são modificadas. Ao parar não fica rastro, e após queda de energia ou desligamento forçado, tudo volta ao normal ao reiniciar.
- **Fragmentação SNI** — Impede que o nome do site fique exposto em conexões HTTPS e HTTP.
- **Lista de exceções / Lista manual** — Escolha quais sites não fragmentar, ou apenas quais fragmentar. Cerca de 160 domínios (bancos, pagamentos, portais, jogos …) já vêm integrados como exceções.
- **Só navegadores** — Aplica a fragmentação apenas aos principais navegadores, sem mexer em jogos e programas de trabalho. Vem ativado desde o início.
- **Pacote falso** — Um método adicional de desvio para redes em que a fragmentação sozinha não basta.
- **Conexão que não cai** — Antes de iniciar, verifica se o servidor DNS está acessível; se o servidor parar de responder durante a execução, a Internet continua e o funcionamento é retomado automaticamente quando o servidor volta. A Internet continua funcionando após suspensão ou troca de Wi-Fi.
- **Relatório** — Tabela de domínios e do resultado aplicado (criptografado, fragmentado, texto puro, via servidor …), separada para DNS e SNI, numa janela própria, com cópia para a área de transferência.
- **Proxy misto** — Apenas os domínios da lista passam por um servidor no exterior. Serve para abrir sites bloqueados com erro 451 que o DNS não consegue contornar; o restante conecta diretamente como sempre, sem perda de velocidade.
- **Início automático · bandeja** — Inicia com o Windows e vai para a área de notificação ao fechar a janela.
- **22 idiomas** — Segue o idioma de exibição do Windows, ou escolha um em **Idioma** nas Configurações.

## Download / Instalação

| Tipo | Link |
|---|---|
| Instalador | [Download](https://down.kilho.net/secretdns?lang=pt) |
| Portátil (ZIP) | [Download](https://down.kilho.net/secretdns?lang=pt&nosetup) |

O instalador executa o SecretDNS ao terminar e registra junto **Iniciar com o Windows**. Na versão portátil, descompacte o ZIP e execute `SecretDNS.exe`. Nos dois casos o SecretDNS pede **permissão de administrador**.

## Como usar

### Primeiros passos

1. Abra o SecretDNS. Quando aparecer a janela de permissão de administrador, clique em **Sim**.
2. Pressione o **botão de cadeado** no centro da tela inicial. Quando o cadeado acende em dourado, está em execução, e o ícone da área de notificação (bandeja) também fica dourado.
3. Use o navegador normalmente. Não há mais nada a fazer.
4. Para desligar, pressione o cadeado de novo ou clique uma vez no ícone da bandeja. Fechar a janela (×) não encerra o programa; ele vai para a bandeja.

O que fica ligado é definido em **Configurações**, aberto pelo botão de **engrenagem** no canto superior direito. Durante a execução as configurações ficam bloqueadas, então pare antes de alterá-las (**Idioma** e **Ver registro** continuam disponíveis em execução). O cadeado no canto superior direito de Configurações executa e para diretamente, sem precisar voltar à tela inicial.

### Organização da tela

**Tela inicial** — No centro, o **botão de cadeado** (executar/parar); no canto superior direito, a **engrenagem** (Configurações); e na barra de status embaixo, a versão. Clicar no logotipo no topo abre o site (o logotipo das outras telas faz o mesmo).

**Configurações** — A seta no canto superior esquerdo volta à tela inicial, e o cadeado no canto superior direito executa/para. O cadeado fica aberto e cinza quando parado, e fechado e dourado em execução.

| Item | O que faz |
|---|---|
| **Config. DNS** — Desativado / Servidores / DNS over HTTPS | Como as consultas DNS são tratadas. O botão **Servidores** nas linhas Servidores e DNS over HTTPS edita a lista de servidores correspondente |
| **Config. SNI** — Desativado / Fragmentar / Fragmentarⓜ | Fragmentar todos os sites (exceto a lista de exceções) ou só os sites da lista manual |
| **Lista de exceções** / **Lista manual** | Escolhendo Fragmentar, aparece logo abaixo dessa linha a caixa da lista de exceções; escolhendo Fragmentarⓜ, aparece abaixo dela a caixa da lista manual. Um domínio por linha |
| **Ativar proxy misto** | Só os domínios da lista passam por um servidor no exterior. Ao marcar, a caixa da lista aparece logo abaixo (requer uma configuração DNS ativa) |
| **Só navegadores** | Aplica fragmentação e pacote falso apenas ao tráfego dos navegadores |
| **Ativar pacote falso** | Método adicional de desvio para redes em que a fragmentação não basta |
| **Ativar relatório** + **Ver registro** | Guarda o relatório. **Ver registro** abre a janela do relatório |
| **Iniciar com o Windows** | Inicia automaticamente na bandeja ao fazer logon. Se estava em execução da última vez, a proteção também é ligada automaticamente |
| **Idioma** | Idioma da interface. Com **Sistema**, segue o idioma de exibição do Windows |

**Servidores DNS** — A lista do lado cujo botão **Servidores** você pressionou (Servidores ou DNS over HTTPS) aparece como tabela, com **Adicionar** · **Editar** · **Excluir** embaixo.

**Janela do relatório** — Três colunas: **Tipo** (DNS · SNI · VPN), **Domínio** e **Aplicado**. Cada linha idêntica é guardada uma só vez, e as linhas com a coluna Aplicado vazia (enviadas sem tratamento) aparecem esmaecidas. **Copiar** / **Copiar tudo** copiam texto separado por tabulações; **Limpar** esvazia a lista. A janela pode ser redimensionada e, ao esconder a janela principal na bandeja e abri-la de novo, a janela do relatório volta junto.

**Ícone da bandeja** — Cinza quando parado, dourado em execução. Um clique alterna executar/parar. O menu do botão direito tem **SecretDNS** (mostrar janela) · **Executar** · **Parar** · **Kilho.net** · **Sair**. Ao passar o mouse aparecem a versão e o estado atual.

### O que fazer quando…

**Um site redireciona para uma página de aviso ou a conexão cai**
Com as configurações padrão (DNS **Servidores** ou **DNS over HTTPS** + SNI **Fragmentar**), basta pressionar o cadeado para resolver a maioria dos casos. Ative o relatório e entre no site: a linha `SNI` deve mostrar **Fragmentar** e a linha `DNS`, **Texto puro** ou **DNS over HTTPS**. Se ainda não funcionar, experimente **Ativar pacote falso** abaixo.

**Um site parou de abrir depois de ligar o SecretDNS (banco, pagamento, login de jogo …)**
O tráfego desse site não tolera fragmentação. Em Configurações, adicione o domínio em uma linha da **lista de exceções**, abaixo da linha **Fragmentar**, e execute de novo.
- Escreva **começando com ponto**, como `.example.com`, para abranger `example.com` e todos os subdomínios (`www.example.com`, `m.example.com`).
- Pode colar a URL da barra de endereços como está: `https://`, `www.` e o caminho final são removidos automaticamente.
- A lista é salva ao clicar fora da caixa, sair de Configurações ou executar, e vale **a partir da próxima execução**. Executando direto pelo cadeado no canto superior direito de Configurações, não é preciso voltar à tela inicial.
- Cerca de 160 domínios — bancos, cartões, pagamentos, portais, compras, jogos, governo (`.go.kr`), escolas (`.ac.kr`) — já vêm integrados como exceções, então não precisa escrevê-los. Eles continuam valendo mesmo se você esvaziar a lista.

**Fragmentar só alguns sites e não mexer no resto**
Mude a Config. SNI para **Fragmentarⓜ** e a caixa da **lista manual** aparece abaixo dessa linha. Só os domínios escritos aqui são fragmentados; todo o resto é enviado intacto. Se só um ou dois sites dão problema, esta opção é mais segura. As regras de escrita são as mesmas da lista de exceções e, se a lista estiver vazia, o programa pede que você informe um domínio antes de executar.

**Criptografar só o DNS, sem fragmentação**
Coloque a Config. DNS em **DNS over HTTPS** e a Config. SNI em **Desativado**. Ao contrário, para deixar o DNS como está e usar só a fragmentação, coloque DNS em **Desativado**. Com os dois desativados aparece "Não há recursos para executar.".

**Aparece "Não foi possível conectar ao servidor DNS criptografado (DoH)."**
Algumas redes de empresas ou escolas têm Internet, mas não alcançam certos servidores DoH. Há duas opções:
- Pressione **Servidores** na linha DNS over HTTPS e marque outro servidor na lista (por exemplo **cloudflare-dns.com** da lista padrão).
- Ou mude a Config. DNS para **Servidores**. Sem criptografia, mas mantém o efeito de usar outro servidor DNS sem alterar as configurações do Windows.

**Usar outro servidor DNS**
Pressione **Servidores** na linha **Servidores** ou **DNS over HTTPS** da Config. DNS para abrir a lista de servidores correspondente.
- Com **Adicionar**, informe **Nome · Endereço 1 · Endereço 2** (reserva, pode ficar vazio). Servidores recebe um endereço IPv4 como `8.8.8.8`; DoH recebe um endereço como `https://1.1.1.1/dns-query` ou `https://dns.google/dns-query`.
- Só os servidores **marcados** são usados. Marcando vários, quando um não responde passa-se automaticamente a outro. Sem nenhum marcado, usa-se o Cloudflare.
- A lista padrão traz Cloudflare (marcado) e Google (desmarcado).
- As alterações valem **a partir da próxima execução**.

**Não afetar jogos nem programas de trabalho**
Deixe **Só navegadores** ativado (vem ativado desde o início). A fragmentação e o pacote falso são aplicados apenas ao tráfego dos principais navegadores, como Chrome · Edge · Firefox · Whale; os outros programas não são tocados. O tratamento do DNS continua valendo para qualquer programa.
Ao contrário, se um programa que não é navegador (um gerenciador de downloads, por exemplo) também precisar de fragmentação, desative **Só navegadores**.

**Continua bloqueado mesmo com fragmentação**
Experimente **Ativar pacote falso**. É um método adicional de desvio para equipamentos de inspeção que a fragmentação sozinha não consegue passar, e não afeta a conexão real.

**Abrir sites bloqueados passando só eles por um servidor no exterior (proxy misto)**
Em países onde a liberdade na Internet não é garantida, um site pode recusar totalmente as conexões vindas daquele país, e o navegador mostra um **erro 451** (Unavailable For Legal Reasons). Isso é raro em países com Internet livre. Nesse caso nem a criptografia DNS nem a fragmentação abrem o site, porque o bloqueio é baseado no país de onde você conecta. O proxy misto faz só esses sites passarem por um servidor de outro país.
Com uma configuração DNS ativa, marque **Ativar proxy misto** e a caixa da lista aparece logo abaixo. Escreva um domínio por linha (`.example.com`, mesma regra da lista de exceções) e execute.
- Só os domínios da lista passam pelo servidor no exterior; o resto conecta diretamente como sempre. Diferente de uma VPN completa, os outros sites mantêm a velocidade normal.
- O servidor é atribuído automaticamente a cada execução e, se não responder, passa-se automaticamente ao seguinte.
- No relatório fica como tipo **VPN**, aplicado **Via servidor**.
- O proxy misto exige uma configuração DNS ativa e é desligado junto ao colocar DNS em Desativado.

**Deixar ligado sempre que o computador é iniciado**
Marque **Iniciar com o Windows** (o instalador já registra isso). Ao fazer logon, ele inicia na bandeja sem janela e, **se da última vez estava em execução**, a proteção também é ligada automaticamente. Se você mesmo parou e saiu, na próxima inicialização ele não liga e fica aguardando.
Se o Wi-Fi demorar a conectar após a inicialização, ele inicia automaticamente assim que a rede estiver disponível.

**Manter ligado depois de fechar a janela**
Ao pressionar fechar (×) ele não encerra, vai para a bandeja, então não há nada a configurar. Para sair de vez, clique com o botão direito no ícone da bandeja → **Sair** (aparece uma confirmação). Ao sair, a proteção também é desligada.

**Mudar o idioma da interface**
Escolha em **Idioma**, no final de Configurações, e a tela muda na hora para esse idioma. Dá para mudar mesmo em execução. Escolhendo **Sistema**, volta a seguir o idioma de exibição do Windows.

**Ver como cada site está sendo tratado agora**
Ative **Ativar relatório** e abra a janela do relatório com **Ver registro**. Os domínios acessados durante a execução vão sendo listados linha a linha. **Ver registro** pode ser pressionado mesmo em execução.

| Tipo | Aplicado | Significado |
|---|---|---|
| DNS | **DNS over HTTPS** | Consultado pelo servidor criptografado |
| DNS | **Texto puro** | Consultado pelo servidor indicado (sem criptografia) |
| SNI | **Fragmentar** | O nome do site foi enviado fragmentado |
| SNI | (vazio) | Enviado sem tratamento: o site está na lista de exceções |
| VPN | **Via servidor** | Passou pelo servidor no exterior via proxy misto |

Com **Copiar tudo** você cola no Bloco de notas ou no Excel com as colunas separadas.

**Por que a Internet não cai mesmo se o servidor DNS não responder**
O SecretDNS verifica antes de executar se o servidor DNS está acessível e, se durante a execução o servidor parar de responder por um tempo, cuida automaticamente para que a Internet não pare. Quando o servidor volta, retorna automaticamente à operação normal; enquanto isso, o estado aparece no ícone da bandeja e no relatório. Não é preciso executar de novo após sair da suspensão ou trocar de Wi-Fi.

**Aparece um aviso sobre o driver**
Em raros casos pode aparecer um aviso pedindo para reiniciar o computador antes de executar. Basta reiniciar como indicado.

**O computador desligou durante a execução**
Não há com o que se preocupar. O SecretDNS não altera as configurações de rede do Windows e só atua enquanto está em execução; por isso, após queda de energia ou desligamento forçado, ao ligar de novo a Internet funciona como sempre. Com **Iniciar com o Windows** ativado, ele reinicia sozinho após o logon.

## Configuração

Alterada em **Configurações** e salva na hora. A maioria vale **a partir da próxima execução**, e as configurações são mantidas nas atualizações.

| Item | Padrão (instalador) | Padrão (portátil) |
|---|---|---|
| Config. DNS | Servidores | Servidores |
| Config. SNI | Fragmentar | Fragmentar |
| Lista de servidores DNS | Servidores: Cloudflare ✓, Google / DNS over HTTPS: Cloudflare ✓, cloudflare-dns.com ✓, Google | igual |
| Ativar proxy misto | Desligado | Desligado |
| Só navegadores | Ligado | Ligado |
| Ativar pacote falso | Desligado | Desligado |
| Ativar relatório | Desligado | Desligado |
| Iniciar com o Windows | Ligado | Desligado |
| Idioma | Sistema | Sistema |

O idioma da interface segue o idioma de exibição do Windows (22 idiomas; nos demais casos, inglês) e pode ser alterado em **Idioma** nas Configurações.

## Requisitos

- Windows 10 ou Windows 11 (32 e 64 bits)
- **Permissão de administrador** — a cada início aparece uma janela de confirmação de permissão.
- Nenhum runtime adicional é necessário.
- Conexão com a Internet — usada para a verificação do servidor DNS e para os avisos de nova versão.

## Atualizações

O SecretDNS **não** se atualiza sozinho. Ao iniciar, verifica se há uma versão nova e mostra um aviso; ao pressionar **Sim**, a página de download é aberta e o programa é encerrado. As novas versões são publicadas manualmente após verificação interna e anunciadas na [página do SecretDNS](https://kilho.net/secretdns). Veja o [aviso sobre a política de atualização](https://en.kilho.net/archives/notice/2940).

## Licença

O SecretDNS é **freeware**. Use gratuitamente e sem restrições em qualquer lugar — empresa, casa, órgãos públicos, escola — e redistribua livremente.

## Links

- Site: <https://kilho.net/secretdns>
- Fórum: <https://kilho.top/forum/qna>
- X (Twitter): <https://www.twitter.com/kilhonet>

© KILHO.NET
