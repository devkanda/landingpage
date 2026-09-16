SIEL — Landing Page v34.27

Correção do carregamento do card Jucelio Silva.

Alterações:
- screenshot remoto via image.thum.io removido;
- novo asset local: assets/jucelio-silva-preview.webp;
- preview local com 824×516px;
- tamanho do asset: 24.9 KB;
- loading="lazy" preservado para não pesar a primeira dobra;
- fetchpriority="low" preservado;
- código JavaScript específico do data-src remoto removido;
- restante da v34.26 preservado.

Efeito esperado:
o card ainda só baixa quando necessário, mas agora a imagem vem do próprio
deploy/Vercel, eliminando o atraso de geração e resposta do serviço externo.
