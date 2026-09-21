# SecretDNS

**Ferramenta gratuita para Windows que contorna a vigilância da Internet (DPI) com DNS over HTTPS e fragmentação SNI, ativada com um único clique.**

[English](README.md) · [한국어](README.ko.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [Español](README.es.md) · Português (Brasil) · [Français](README.fr.md)

> Este documento é uma tradução. Em caso de divergência, a [versão em coreano](README.ko.md) prevalece.

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%2F%2011-0078D4)
![License](https://img.shields.io/badge/license-Freeware-brightgreen)
![Version](https://img.shields.io/badge/version-4.0.5-blue)
[![Download](https://img.shields.io/badge/download-kilho.net-orange)](https://down.kilho.net/secretdns?lang=pt)

![Tela do SecretDNS](images/secretdns-en.webp)

> A interface do programa não tem tradução para português; ela é exibida em inglês. Os nomes de botões e opções abaixo aparecem como na tela.

## Visão geral

Ao abrir um site, o computador envia duas coisas em texto puro: uma **consulta DNS** pedindo o endereço IP do site e o **nome do site (SNI)**, que vai no primeiro pacote de toda conexão HTTPS. Os equipamentos de inspeção (DPI) das operadoras ou administradores de rede leem os dois para saber qual site você está visitando e, se quiserem, cortam a conexão ou redirecionam para uma página de aviso.

O SecretDNS fecha as duas brechas com um único clique em **Run**.

- **DNS** — Trata as consultas DNS do computador com **criptografia (DoH)** por meio de um servidor como o Cloudflare. As configurações de rede do Windows não são tocadas; por isso, ao parar o programa tudo volta ao normal na hora, e se o computador desligar de repente durante a execução, ao reiniciar a Internet funciona como sempre, sem deixar rastro.
- **SNI** — **Impede que o nome do site fique exposto aos equipamentos de inspeção** nas conexões HTTPS. A conexão com o site funciona normalmente e, como só a parte do nome é tratada, quase não há perda de velocidade.

Sites que param de funcionar quando fragmentados (bancos, meios de pagamento) passam intactos graças a uma **lista de exceções** integrada, e o **Report** mostra como cada site foi tratado. Para sites que o desvio de DNS não consegue abrir — como o **erro 451**, comum em países sem liberdade na Internet, em que o próprio site recusa conexões vindas daquele país — o **Mixed Proxy** faz só esses sites passarem por outro país. Apenas os domínios que você indicar passam por lá, então o resto da sua Internet mantém a velocidade total.

O SecretDNS não é uma VPN. Ele não esconde seu endereço IP nem criptografa todo o tráfego: trata apenas os dois pontos usados para vigilância, DNS e SNI.

## Principais recursos

- **Um clique** — Basta pressionar **Run** na tela inicial. Um clique no ícone da bandeja também liga e desliga.
- **DNS over HTTPS** — Cloudflare por padrão. Adicione seus próprios servidores e marque vários; o SecretDNS alterna entre eles automaticamente. Há também o modo **Servers**, que usa um servidor DNS sem criptografia (ex.: 1.1.1.1).
- **Sem alterar as configurações do Windows** — As configurações DNS do adaptador de rede não são modificadas. Ao parar não fica rastro, e após queda de energia ou desligamento forçado, tudo volta ao normal ao reiniciar.
- **Fragmentação SNI** — Impede que o nome do site fique exposto em conexões HTTPS e HTTP.
- **Lista de exceções / Lista manual** — Escolha quais sites não fragmentar, ou apenas quais fragmentar. Cerca de 160 domínios (bancos, pagamentos, portais, jogos …) já vêm integrados como exceções.
- **Somente navegadores** — Aplica a fragmentação apenas aos principais navegadores, sem mexer em jogos e programas de trabalho.
- **Pacote falso** — Um método adicional de desvio para redes em que a fragmentação sozinha não basta.
- **Conexão que não cai** — Antes de iniciar, verifica se o servidor DNS está acessível; se o servidor parar de responder durante a execução, a Internet continua e a criptografia é retomada automaticamente quando o servidor volta. A Internet continua funcionando após suspensão ou troca de Wi-Fi.
- **Report** — Tabela de domínios e do resultado aplicado (criptografado, fragmentado, texto puro, via servidor …), separada para DNS e SNI, com cópia para a área de transferência.
- **Mixed Proxy** — Apenas os domínios da lista passam por um servidor no exterior. Serve para abrir sites bloqueados com erro 451 que o DNS não consegue contornar; o restante conecta diretamente como sempre, sem perda de velocidade.
- **Início automático · bandeja** — Inicia com o Windows e minimiza para a área de notificação ao fechar.
- **8 idiomas** — Coreano · inglês · japonês · chinês · russo · italiano · francês · espanhol. Segue o idioma de exibição do Windows.

## Download / Instalação

| Tipo | Link |
|---|---|
| Instalador | [Download](https://down.kilho.net/secretdns?lang=pt) |
| Portátil (ZIP) | [Download](https://down.kilho.net/secretdns?lang=pt&nosetup) |

O instalador executa o SecretDNS ao terminar e o registra para **iniciar com o Windows**. Na versão portátil, descompacte o ZIP e execute `SecretDNS.exe`. Nos dois casos o SecretDNS pede **permissão de administrador**.

Diferença entre as versões: o recurso **Mixed Proxy** está incluído apenas na versão com instalador (na portátil a opção fica bloqueada).

## Como usar

### Fluxo básico

1. Abra o SecretDNS. Quando aparecer a janela de permissão de administrador, clique em **Sim**.
2. Pressione **Run** na tela inicial. O botão mostra por um instante **Checking network**, depois passa a **Running**, e o ícone da área de notificação (bandeja) muda para o estado ligado.
3. Use o navegador normalmente. Não há mais nada a fazer.
4. Para desligar, pressione o botão **Running** de novo ou clique uma vez no ícone da bandeja. Fechar a janela encerra o programa (com **Minimize to tray on quit** ativado, ele vai para a bandeja).

O que fica ligado é definido na aba **Config**. Durante a execução as configurações ficam bloqueadas, então pare antes de alterá-las (a lista do Mixed Proxy é a exceção: vale na hora, mesmo em execução).

### Organização da tela

No topo ficam as abas **Home · Config · Report · Donate**; clicar no logotipo à direita abre o site.

**Config**

| Item | O que faz |
|---|---|
| **DNS Config** — Disabled / Servers / DNS over HTTPS | Como as consultas DNS são tratadas. **[…]** abre a janela **DNS servers** para editar a lista de servidores |
| **SNI Config** — Disabled / Fragment / Fragmentⓜ | Fragmentar todos os sites (exceto a lista de exceções) ou só os sites da lista manual |
| Lista **Exception** / **Manual** | Lista de domínios que muda conforme a configuração SNI. Um domínio por linha |
| **Minimize to tray on start** | Inicia na bandeja ao fazer logon (início com o Windows). Se estava em execução da última vez, a proteção também é ligada automaticamente |
| **Minimize to tray on quit** | Fechar a janela não encerra; vai para a bandeja |
| **Enable Mixed Proxy** + **[…]** | Só os domínios da lista passam por um servidor no exterior. **[…]** edita a lista (versão com instalador, requer uma configuração DNS ativa) |
| **Enable Report** | Guarda registros na aba Report |
| **Browsers only** | Aplica fragmentação e pacote falso apenas ao tráfego dos navegadores |
| **Enable Fake Packet** | Método adicional de desvio para redes em que a fragmentação não basta |

**Report** — Três colunas: **Type** (DNS · SNI · VPN), **Domain** e **Applied**. Cada linha idêntica é guardada uma só vez, e as linhas com a coluna Applied vazia (enviadas sem tratamento) aparecem esmaecidas. **Copy** / **Copy(All)** copiam texto separado por tabulações; **Clear** esvazia a lista.

**Ícone da bandeja** — Um clique alterna Run/Stop. O menu do botão direito tem **SecretDNS** (mostrar janela) · **Run** · **Stop** · **Kilho.net** · **Quit**. Ao passar o mouse aparecem a versão e o estado atual.

### O que fazer quando…

**Um site redireciona para uma página de aviso ou a conexão cai**
Com as configurações padrão (DNS **DNS over HTTPS** ou **Servers** + SNI **Fragment**), basta pressionar **Run** para resolver a maioria dos casos. Ative o Report e entre no site: a linha `SNI` deve mostrar **Fragment** e a linha `DNS`, **DNS over HTTPS**. Se ainda não funcionar, experimente **Enable Fake Packet** abaixo.

**Um site parou de abrir depois de ligar o SecretDNS (banco, pagamento, login de jogo …)**
O tráfego desse site não tolera fragmentação. Adicione o domínio em uma linha da lista **Exception** em Config e execute de novo.
- Escreva **começando com ponto**, como `.example.com`, para abranger `example.com` e todos os subdomínios (`www.example.com`, `m.example.com`).
- Pode colar a URL da barra de endereços como está: `https://`, `www.` e o caminho final são removidos automaticamente.
- A lista é salva ao clicar em outro lugar e vale **a partir da próxima execução**.
- Cerca de 160 domínios — bancos, cartões, pagamentos, portais, compras, jogos, governo (`.go.kr`), escolas (`.ac.kr`) — já vêm integrados como exceções, então não precisa escrevê-los. Eles continuam valendo mesmo se você esvaziar a lista.

**Fragmentar só alguns sites e não mexer no resto**
Mude a configuração SNI para **Fragmentⓜ** e a lista abaixo passa a ser a lista **Manual**. Só os domínios escritos aqui são fragmentados; todo o resto é enviado intacto. Se só um ou dois sites dão problema, esta opção é mais segura. As regras de escrita são as mesmas da lista de exceções.

**Criptografar só o DNS, sem fragmentação**
Coloque a configuração DNS em **DNS over HTTPS** e a SNI em **Disabled**. Ao contrário, para deixar o DNS como está e usar só a fragmentação, coloque DNS em **Disabled**. Com os dois desativados aparece "There are no features to execute.".

**Aparece "Cannot connect to the encrypted (DoH) DNS server."**
Algumas redes de empresas ou escolas têm Internet, mas não alcançam certos servidores DoH. Há duas opções:
- Pressione **[…]** ao lado da configuração DNS e, na lista **DNS over HTTPS**, marque outro servidor (por exemplo **cloudflare-dns.com** da lista padrão).
- Ou mude a configuração DNS para **Servers**. Sem criptografia, mas mantém o efeito de usar outro servidor DNS sem alterar as configurações do Windows.

**Usar outro servidor DNS**
Pressione **[…]** ao lado da configuração DNS para abrir a janela **DNS servers**. À esquerda fica a lista **Servers** (endereços IP) e à direita a lista **DNS over HTTPS**.
- Com **Add**, informe **Name · Address 1 · Address 2** (reserva, pode ficar vazio). Servers recebe um endereço IPv4 como `8.8.8.8`; DoH recebe um endereço como `https://1.1.1.1/dns-query` ou `https://dns.google/dns-query`.
- Só os servidores **marcados** são usados. Marcando vários, quando um não responde passa-se automaticamente a outro. Sem nenhum marcado, usa-se o Cloudflare.
- A lista padrão traz Cloudflare (marcado) e Google (desmarcado).
- As alterações valem **a partir da próxima execução**.

**Não afetar jogos nem programas de trabalho**
Ative **Browsers only**. A fragmentação e o pacote falso são aplicados apenas ao tráfego dos principais navegadores, como Chrome · Edge · Firefox · Whale; os outros programas não são tocados. A criptografia DNS continua valendo para qualquer programa.

**Continua bloqueado mesmo com fragmentação**
Experimente **Enable Fake Packet**. É um método adicional de desvio para equipamentos de inspeção que a fragmentação sozinha não consegue passar, e não afeta a conexão real.

**Abrir sites bloqueados passando só eles por um servidor no exterior (Mixed Proxy)**
Em países onde a liberdade na Internet não é garantida, um site pode recusar totalmente as conexões vindas daquele país, e o navegador mostra um **erro 451** (Unavailable For Legal Reasons). Isso é raro em países com Internet livre. Nesse caso nem a criptografia DNS nem a fragmentação abrem o site, porque o bloqueio é baseado no país de onde você conecta. O Mixed Proxy faz só esses sites passarem por um servidor de outro país.
Na versão com instalador, com uma configuração DNS ativa, marque **Enable Mixed Proxy** e pressione **[…]** para abrir a janela da lista. Escreva um domínio por linha (`.example.com`, mesma regra da lista de exceções) e pressione **OK**.
- Só os domínios da lista passam pelo servidor no exterior; o resto conecta diretamente como sempre. Diferente de uma VPN completa, os outros sites mantêm a velocidade normal.
- O servidor é atribuído automaticamente a cada execução e, se não responder, passa-se automaticamente ao seguinte.
- A lista vale **mesmo em execução**.
- No Report fica como tipo **VPN**, aplicado **Via server**.
- O Mixed Proxy exige uma configuração DNS ativa e é desligado junto ao colocar DNS em Disabled.

**Deixar ligado sempre que o computador é iniciado**
Marque **Minimize to tray on start** (o instalador já registra isso). Ao fazer logon, ele inicia na bandeja sem janela e, **se da última vez estava em execução**, a proteção também é ligada automaticamente. Se você mesmo parou e saiu, na próxima inicialização ele não liga e fica aguardando.
Se o Wi-Fi demorar a conectar após a inicialização, ele inicia automaticamente assim que a rede estiver disponível.

**Manter ligado depois de fechar a janela**
Ative **Minimize to tray on quit**; ao pressionar fechar (×) ele não encerra, vai para a bandeja. Para sair de vez, clique com o botão direito no ícone da bandeja → **Quit** (aparece uma confirmação). Ao sair, a proteção também é desligada.

**Ver como cada site está sendo tratado agora**
Ative **Enable Report** e abra a aba **Report**. Os domínios acessados durante a execução vão sendo listados linha a linha.

| Type | Applied | Significado |
|---|---|---|
| DNS | **DNS over HTTPS** | Consultado pelo servidor criptografado |
| DNS | **Plaintext** | Consultado pelo servidor indicado (sem criptografia) |
| SNI | **Fragment** | O nome do site foi enviado fragmentado |
| SNI | (vazio) | Enviado sem tratamento: o site está na lista de exceções |
| VPN | **Via server** | Passou pelo servidor no exterior via Mixed Proxy |

Com **Copy(All)** você cola no Bloco de notas ou no Excel com as colunas separadas.

**Por que a Internet não cai mesmo se o servidor DNS não responder**
O SecretDNS verifica antes de executar se o servidor DNS está acessível e, se durante a execução o servidor parar de responder por um tempo, cuida automaticamente para que a Internet não pare. Quando o servidor volta, retorna automaticamente à operação normal; enquanto isso, o estado aparece no ícone da bandeja e no Report. Não é preciso executar de novo após sair da suspensão ou trocar de Wi-Fi.

**Aparece um aviso sobre o driver**
Em raros casos pode aparecer um aviso pedindo para reiniciar o computador antes de executar. Basta reiniciar como indicado.

**O computador desligou durante a execução**
Não há com o que se preocupar. O SecretDNS não altera as configurações de rede do Windows e só atua enquanto está em execução; por isso, após queda de energia ou desligamento forçado, ao ligar de novo a Internet funciona como sempre. Com o início automático ativado, ele reinicia sozinho após o logon.

## Configuração

Alterada na aba **Config** e salva na hora. A maioria vale **a partir da próxima execução**, e as configurações são mantidas nas atualizações.

| Item | Padrão (instalador) | Padrão (portátil) |
|---|---|---|
| SNI Config | Fragment | Fragment |
| Lista de servidores DNS | Servers: Cloudflare ✓, Google / DoH: Cloudflare ✓, cloudflare-dns.com ✓, Google | igual |
| Minimize to tray on start | Ligado | Desligado |
| Minimize to tray on quit | Ligado | Desligado |
| Enable Mixed Proxy | Desligado | Indisponível |
| Enable Report | Desligado | Desligado |
| Browsers only | Desligado | Desligado |
| Enable Fake Packet | Desligado | Desligado |

O idioma da interface segue o idioma de exibição do Windows (coreano · inglês · japonês · chinês · russo · italiano · francês · espanhol; nos demais casos, inglês).

## Requisitos

- Windows 10 ou Windows 11 (32 e 64 bits)
- **Permissão de administrador** — a cada início aparece uma janela de confirmação de permissão.
- Nenhum runtime adicional é necessário.
- Conexão com a Internet — usada para a verificação do servidor DNS e para os avisos de nova versão.

## Atualizações

O SecretDNS **não** se atualiza sozinho. Ao iniciar, verifica se há uma versão nova e mostra um aviso; ao pressionar **Yes**, a página de download é aberta e o programa é encerrado. As novas versões são publicadas manualmente após verificação interna e anunciadas na [página do SecretDNS](https://v2.kilho.net/secretdns). Veja o [aviso sobre a política de atualização](https://en.kilho.net/archives/notice/2940).

**Histórico de versões**

| Versão | Data | Mudanças |
|---|---|---|
| 4.0.5 | 2026-09-15 | Troca automática de servidor do Mixed Proxy para conexões mais estáveis; uso de VPN mais fácil de identificar no Report |
| 4.0.4 | 2026-09-14 | Atualização e início automático mais confiáveis; Mixed Proxy reformulado (janela de edição de domínios, configurações salvas); janela de servidores DNS para adicionar e escolher servidores; melhor conectividade de DNS criptografado em algumas operadoras (endereços por nome, novo ponto de conexão Cloudflare); orientação para escolher outro servidor em caso de falha; textos do Report mais claros |
| 4.0.2 | 2026-09-04 | Corrigidas interrupções intermitentes da Internet em alguns ambientes; troca automática de servidores DNS instáveis; os sites continuam abrindo durante erros temporários de DNS; a conexão criptografada é restaurada automaticamente quando a rede se estabiliza |
| 4.0.1 | 2026-08-25 | Corrigida a falta de Internet logo após a inicialização em alguns PCs; melhor conectividade após suspensão, VPN ou troca de Wi-Fi; recuperação automática em quedas de Internet; exibição do estado de espera e recuperação |

## Licença

O SecretDNS é **freeware**. Use gratuitamente e sem restrições em qualquer lugar — empresa, casa, órgãos públicos, escola — e redistribua livremente.

## Links

- Site: <https://v2.kilho.net/secretdns>
- Fórum: <https://groups.google.com/g/kilhonet>
- X (Twitter): <https://www.twitter.com/kilhonet>

© KILHO.NET
