# Simulador de Biorreator

Simulador didático de cultivos microbianos em biorreator: o usuário informa os parâmetros e o app devolve a modelagem (curvas de biomassa, substrato, produto, oxigênio dissolvido e mais), recalculada em tempo real.

## O que ele faz

- **Modos de operação:** batelada, batelada alimentada (vazão constante ou exponencial) e contínuo (quimiostato).
- **Cinética:** Monod ou Haldane (inibição por substrato), produto por Luedeking–Piret, inibição por produto (Levenspiel), manutenção e morte celular.
- **Ambiente:** efeito de temperatura e pH por modelos cardinais (Rosso), solubilidade de O₂ em função de T e oxigênio dissolvido com kLa fixo ou cascata de controle de OD.
- **Estado estacionário do quimiostato:** curvas X\*, S\*, P\* vs. D, D crítico (washout) e D de máxima produtividade.
- **Agitação e aeração:** escolha do impelidor (Rushton, pás inclinadas, hidrofólio, hélice marinha), número de impelidores, geometria, rpm e vvm. O app calcula potência, P/V, kLa (van't Riet), inundação do impelidor, Reynolds, velocidade na ponta e tempo de mistura; a cascata de OD passa a atuar sobre a rotação.
- **Ajuste a dados:** kLa pelo método dinâmico (gassing-out) e μmax, Ks, Yx/s, α, β e X₀ a partir de um ensaio em batelada, por mínimos quadrados, com IC 95% e classificação de identificabilidade. Os valores ajustados vão para o simulador com um clique.
- **Diagnóstico automático** (O₂ limitante, lavagem, inibição, acúmulo de substrato) e verificação do balanço de massa.
- **Presets:** *E. coli*, *S. cerevisiae* e *L. delbrueckii* (valores ilustrativos de literatura).
- Comparação de cenários, tabela de dados e exportação em CSV.

## Rodar localmente

É um arquivo HTML único, sem build nem dependências: abra `index.html` no navegador.

## Deploy no Netlify

Em **Add new site → Import an existing project**, conecte este repositório. Não há comando de build; o diretório de publicação é a raiz (`.`). Cada push na `main` publica automaticamente.

## Modelo

As equações, hipóteses e referências estão na aba **Modelo** do próprio app. Integração numérica por Runge–Kutta de 4ª ordem; o OD é tratado em quase-estado-estacionário.

Ferramenta de ensino. Para uso em projeto, os parâmetros precisam ser ajustados a dados experimentais do sistema real.
