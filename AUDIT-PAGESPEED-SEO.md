# Auditoria PageSpeed & SEO — Siel v34.26

Base: v34.25  
Escopo aplicado: Performance/Core Web Vitals, SEO técnico, Acessibilidade, Boas Práticas e experiência mobile.

## Baseline local
- HTML: 15.0 KB
- CSS: 78.7 KB
- Hero PNG desktop: 1183.3 KB
- Meta robots: ausente
- Open Graph/Twitter: ausentes
- Canonical: ausente
- Sitemap: ausente
- robots.txt: ausente
- Favicon/apple-touch icon: ausentes
- Skip link: ausente
- 1 H1 e hierarquia H1 → H2 → H3: OK
- Imagens abaixo da dobra com lazy loading: OK
- Imagens locais com width/height: OK
- LCP/background da hero com preload: OK
- Google Fonts com display=swap e carregamento não bloqueante: OK
- prefers-reduced-motion: OK

## Melhorias aplicadas

### Performance
- Hero desktop recomprimida em PNG de forma lossless: 1183.3 KB → 1087.2 KB.
- Criada hero específica para telas <= 520 px: 420.5 KB, evitando carregar o PNG desktop inteiro no celular.
- Preload da hero separado por media query para desktop/mobile.
- Mantidos lazy loading e fetchpriority baixo nos projetos.
- Preview remoto do Jucelio continua carregando só quando se aproxima da viewport.

### SEO técnico
- Title refinado para: `Siel — Web Design | Sites com a cara do seu negócio`.
- Description com 129 caracteres e linguagem natural.
- Meta robots adicionada.
- Open Graph básico: type, locale, site_name, title e description.
- Twitter Card básico: card, title e description.
- robots.txt criado e liberando o rastreamento público.
- Favicon e Apple Touch Icon adicionados.

### Acessibilidade
- Skip link “Pular para o conteúdo”.
- Foco visível global para links e botões.
- Rótulos mais completos em links que abrem nova aba.
- Imagens que ficam dentro de links já rotulados passaram a ser decorativas (`alt=""`), evitando leitura duplicada.
- `aria-pressed` removido do toggle de tema para não comunicar um estado ambíguo; o `aria-label` dinâmico permanece.
- Alvos do footer ampliados para pelo menos 44 px.
- Microtexto `WEB DESIGN` aumentado discretamente para legibilidade.

### Boas práticas / segurança
- `rel="noopener noreferrer"` normalizado nos links externos.
- `referrerpolicy="no-referrer"` no screenshot externo do Jucelio.
- Handler inline `onerror` removido e movido para JS.
- `vercel.json` com:
  - X-Content-Type-Options: nosniff
  - Referrer-Policy: strict-origin-when-cross-origin
  - Permissions-Policy para câmera/microfone/geolocalização
  - X-Frame-Options: SAMEORIGIN

## Itens não aplicados de propósito

### Canonical / sitemap.xml / og:url / og:image absoluto
Não foram inventados porque dependem do **URL de produção definitivo**. Usar um domínio/preview errado no canonical pode prejudicar SEO em vez de ajudar.

Quando o domínio final estiver definido, adicionar:
- `<link rel="canonical" href="https://DOMINIO/">`
- `og:url`
- `og:image` absoluto
- `sitemap.xml` com URL absoluta
- `Sitemap:` em robots.txt
- JSON-LD WebSite/ProfessionalService com `url` real

### Conversão da hero para WebP/AVIF
Não aplicada. A versão anterior mostrou perda visual perceptível e a qualidade da hero é parte importante da identidade. Aqui foi usada **compressão PNG lossless** + asset mobile separado.

### CSP/HSTS rígidos
Não aplicados nesta etapa para evitar regressões com scripts inline, Google Fonts e configuração futura de domínio. Os headers seguros e de baixo risco foram adicionados primeiro.

## Validação recomendada após deploy
Rodar PageSpeed/Lighthouse em mobile e desktop na URL de produção e comparar:
- Performance
- Accessibility
- Best Practices
- SEO
- FCP / LCP / CLS / TBT ou INP

Meta prática: >= 90 em todas as categorias sem sacrificar a qualidade visual.


## Validação local executada
- HTML parseado sem erro.
- 1 único H1.
- Hierarquia de headings sem saltos.
- Nenhum ID duplicado.
- Nenhuma imagem sem atributo `alt`.
- Todas as imagens têm `width` e `height`.
- Nenhum link `target="_blank"` sem `noopener noreferrer`.
- Nenhuma referência local quebrada.
- JavaScript inline validado com `node --check`: sem erro de sintaxe.
- CSS validado com parser: sem erro de sintaxe.

Observação: o ambiente atual não permitiu executar Lighthouse/Chrome contra servidor local, então a nota final deve ser medida após o deploy na URL pública. A auditoria desta versão foi aplicada sobre código e assets, com validação estática e de sintaxe.
