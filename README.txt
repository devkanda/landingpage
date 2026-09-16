SIEL — Landing Page v34.10

Correção definitiva do fundo da hero.

Problema encontrado:
- regras antigas `html[data-theme="dark"] .hero` e `light`
  tinham mais especificidade que `.hero`;
- por isso o gradiente antigo sobrescrevia o novo asset,
  mesmo com `!important`.

Correção:
- imagem aplicada diretamente no seletor do tema;
- overlays praticamente zerados;
- layers auxiliares da hero não podem mais cobrir o asset;
- ondas do arquivo hero-abstract-dark.png ficam visíveis;
- estrutura, header, CTAs, portfólio e restante do site preservados.
