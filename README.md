# thIAguinho IPTV WEB — Samsung UN43J5200

Reprodutor web **experimental**, feito em HTML/CSS/JavaScript compatível com sintaxe ES5, voltado ao navegador antigo da Samsung Série J (Samsung Legacy/Orsay).

**Não é APK nem aplicativo instalado no Smart Hub.** O acesso é pelo navegador da TV.

## Link esperado

https://tsvalencio-ia.github.io/IPTV-/

O endereço só funciona depois que o Pages estiver habilitado e a publicação do Actions terminar com sucesso.

## Ativar o Pages pelo celular

1. Entre no repositório `tsvalencio-IA/IPTV-`.
2. Abra **Settings → Pages**.
3. Em **Build and deployment → Source**, selecione **GitHub Actions**.
4. Entre na aba **Actions**, abra **Publicar IPTV Web no GitHub Pages** e, se necessário, use **Run workflow**.
5. Aguarde a conclusão de um deploy com status verde e então acesse o endereço acima pela TV.

Se o GitHub solicitar liberação de workflows, conceda apenas a esse repositório.

## Primeiros testes na TV

1. Abra o link da página pelo navegador.
2. Clique em **Verificar navegador** e veja MP4, HLS nativo, MediaSource e Promise.
3. Clique em **Testar vídeo MP4 público** e pressione Reproduzir, se necessário.
4. Clique em **Testar transmissão HLS pública**.
5. Só depois configure o serviço de IPTV, se autorizado.

Se MP4 funcionar, mas HLS não, isso indica que o navegador pode precisar de outro formato. Se ambos falharem, verifique HTTPS/certificados, codecs e o player HTML5 da TV.

## Formatos de entrada

- **Link direto**: MP4 ou HLS (M3U8).
- **Playlist M3U**: cole o conteúdo, selecione um arquivo local quando o navegador suportar ou cole uma URL de lista disponível com CORS.
- **Conta Xtream compatível**: informe servidor, usuário e senha na própria página; tenta os endpoints `player_api.php` (canais ao vivo, categorias) e compõe links de reprodução conforme o formato escolhido.

Os testes MP4 e HLS públicos servem apenas para diagnosticar compatibilidade.

## Dados privados e segurança

- **Não** inclua credenciais, links IPTV privados, tokens, arquivos M3U de assinatura nem screenshots com senhas no repositório, nos arquivos do GitHub Pages, nos logs de Actions ou nos issues.
- A página **não envia dados à GitHub Actions**. O navegador faz requisições diretamente ao servidor IPTV que você informou.
- Os valores digitados e os canais obtidos ficam na memória da aba. Não há `localStorage`, cookies do site, telemetria ou backend de contas; atualizar ou fechar a página limpa a lista e as credenciais.
- Não use uma URL IPTV como parâmetro da página (querystring ou fragmento), nem a cole em local público.
- **Atenção:** links do tipo Xtream incluem credenciais nos endereços de chamada ao fornecedor e nos links de mídia, por exigência desse protocolo. Esses endereços podem ficar no histórico/cache/logs do **próprio fornecedor** e do navegador/dispositivo. Prefira o serviço com **HTTPS** e não utilize em dispositivos compartilhados.
- Caso você tenha exposto uma senha em local não confiável, solicite troca ao provedor.

## Limitações técnicas importantes

- O GitHub Pages serve arquivos estáticos e **não oferece retransmissão/proxy IPTV**.
- Em geral, páginas HTTPS **não conseguem buscar listas e streams HTTP**: conteúdo misto bloqueado. Peça ao serviço um endpoint HTTPS, se disponível.
- Carregamento de listas e chamadas de `player_api.php` exigem **CORS** liberado pelo servidor. Um player estático não consegue impor CORS a outro domínio.
- O navegador Samsung Legacy pode não suportar a reprodução HLS via HTML5 ou as APIs necessárias ao `hls.js`. Para navegadores modernos com MSE e Promise, o player busca `hls.js` via CDN; na Samsung a prioridade é a reprodução nativa.
- MPEG-TS direto (`.ts`), DRM e codecs específicos podem falhar mesmo que o site abra.
- O projeto ainda **não foi validado na TV física**. Não é correto afirmar compatibilidade definitiva sem testes reais.

## Arquivos

- `index.html`: interface, diagnósticos, playlist e reprodução.
- `.github/workflows/pages.yml`: workflow de deploy no GitHub Pages.

Nenhuma modificação é feita em outros repositórios.

**Uso responsável:** conecte apenas transmissões para as quais você tenha autorização.
