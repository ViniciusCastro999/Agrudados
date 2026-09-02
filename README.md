# Agrudados

Aplicação desktop em Java Swing para o cálculo e a visualização de **estatística descritiva de dados agrupados e não agrupados**. O usuário informa um conjunto de valores e o programa calcula as medidas de tendência central e de dispersão, monta a tabela de distribuição de frequências e gera gráficos (histograma, polígono de frequências e ogiva).

O nome vem de *"(dados) agrupados"*.

## Funcionalidades

### Medidas de tendência e dispersão
- **Central:** média, moda (identificando conjuntos amodais, bimodais e multimodais) e mediana.
- **Dispersão:** desvio médio, variância, desvio padrão, amplitude e coeficiente de variação.
- Suporte a conjunto **amostral** (denominador `n - 1`) e **populacional** (denominador `n`).
- Entrada dos valores por tabela editável, com opções de alterar, excluir, ordenar e apagar o conjunto.

### Análise de dados / distribuição de frequências
- Montagem automática da tabela de distribuição de frequências:
  - número de classes pela regra de Sturges (`1 + 3,3 · log₁₀ n`);
  - intervalo de classe, ponto médio, frequência simples e acumulada, frequência relativa (absoluta) e frequência relativa acumulada.
- Gráficos gerados com JFreeChart:
  - **Histograma** (frequência ou frequência relativa);
  - **Polígono de frequências**;
  - **Ogiva** (frequência acumulada).

### Fórmulas
- Tela de referência com a definição, a fórmula e um exemplo resolvido de cada medida.

## Tecnologias

- **Java 8** (`source`/`target` 1.8)
- **Swing** para a interface (Look and Feel Nimbus)
- **NetBeans** — projeto Ant (`build.xml` / `nbproject/`), com telas construídas no GUI Builder (`.form`)
- **[JFreeChart 1.5.0](https://www.jfree.org/jfreechart/)** para os gráficos
- Bibliotecas Swing Layout Extensions e AbsoluteLayout (fornecidas pelo NetBeans)

## Estrutura do projeto

```
Agrudados/
├── build.xml, manifest.mf, nbproject/   → configuração do projeto NetBeans/Ant
├── Pacote de Icones/                     → ícones usados na interface
└── src/
    ├── agrudados/            → telas Swing
    │   ├── TelaInicial            (janela principal / menu)
    │   ├── TelaMedidasDeTendencia (entrada de dados + medidas central/dispersão)
    │   ├── TelaAnaliseDeDados     (tabela de frequências + gráficos)
    │   └── TelaFormulas          (referência de fórmulas)
    ├── estatistica/         → lógica dos cálculos
    │   ├── Calculos              (classe base: dados de entrada e resultados)
    │   ├── Central              (média, moda, mediana)
    │   ├── Dispersao            (desvio médio, variância, desvio padrão, amplitude, CV)
    │   └── DistribuicaoDeFrequencias (classes, intervalos, frequências, ponto médio)
    ├── modelostabelas/      → modelos das JTable (ElementosModel, elementos)
    └── imagens/             → ícones e imagens de fundo
```

`main.class`: `agrudados.TelaInicial`

## Como compilar e executar

### Pré-requisitos
- JDK 8 ou superior
- Apache Ant (ou o NetBeans, que já o inclui)
- `jfreechart-1.5.0.jar` — o projeto espera o arquivo **um nível acima** da pasta `Agrudados/`
  (referência em `nbproject/project.properties`: `..\jfreechart-1.5.0.jar`)

### Pelo NetBeans
Abra a pasta `Agrudados/` como projeto e use **Run** (F6). Ajuste a referência da biblioteca JFreeChart caso o NetBeans peça.

### Pela linha de comando
```sh
cd Agrudados
ant clean jar
java -jar dist/Agrudados.jar
```

## Observações

- Os cálculos assumem que o conjunto de dados foi informado em **ordem crescente** (mediana, amplitude e montagem das classes dependem disso); use a opção *Ordenar tabela* antes de calcular.
- O arquivo `.gitignore` contém marcadores de conflito de merge não resolvidos que devem ser limpos.

## Licença

Domínio público — veja [LICENSE](LICENSE) ([Unlicense](http://unlicense.org)).

## Autor

Vinicius Cardoso de Castro
