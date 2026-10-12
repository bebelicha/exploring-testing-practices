# Explorando Práticas de Teste

Neste exercício, vamos explorar práticas de teste em sistemas reais utilizando a ferramenta [TestMiner](https://andrehora.github.io/testminer).

O TestMiner permite visualizar e analisar testes de software em repositórios do GitHub, fornecendo dados sobre como os projetos organizam seus testes, como eles evoluem entre versões e quais bibliotecas de teste são utilizadas.
Explore a ferramenta antes de começar para se familiarizar com seu funcionamento.

Mais detalhes no GitHub da ferramenta: https://github.com/andrehora/testminer.

---

## Passo 1: Selecionar um repositório

Escolha um repositório real que possua testes de software.
Abaixo estão alguns links para ajudá-lo a encontrar projetos interessantes:

- Python: https://github.com/topics/python?l=python
- JavaScript: https://github.com/topics/javascript?l=javascript
- TypeScript: https://github.com/topics/typescript?l=typescript
- Java: https://github.com/topics/java?l=java

- Tópicos: [ai](https://andrehora.github.io/testminer/#topic:ai), [llm](https://andrehora.github.io/testminer/#topic:llm), [api](https://andrehora.github.io/testminer/#topic:api), [nodejs](https://andrehora.github.io/testminer/#topic:nodejs), [android](https://andrehora.github.io/testminer/#topic:android)

- Por organização: [Google](https://andrehora.github.io/testminer/#google), [Microsoft](https://andrehora.github.io/testminer/#microsoft), [Apple](https://andrehora.github.io/testminer/#apple), [Facebook](https://andrehora.github.io/testminer/#facebook), [Netflix](https://andrehora.github.io/testminer/#netflix), 
[GitHub](https://andrehora.github.io/testminer/#github), [Apache](https://andrehora.github.io/testminer/#apache), [HuggingFace](https://andrehora.github.io/testminer/#huggingface)

## Passo 2: Explorar o repositório selecionado

Busque o repositório escolhido no [TestMiner](https://andrehora.github.io/testminer) e analise os dados de teste gerados pela ferramenta.

## Passo 3: Explicar uma prática de teste

Escolha uma prática ou dado de teste relevante e explique com suas próprias palavras.

---

## Instruções de entrega

1. Faça um `fork` deste repositório (saiba mais sobre forks [aqui](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)).
2. Responda às questões abaixo diretamente neste arquivo `README.md` do seu fork. Pode adicionar imagens para enriquecer sua explicação.
3. No Moodle, submeta apenas a URL do seu fork.

---

## Respostas
Repositório: `https://github.com/godotengine/godot`

URL TestMiner: `https://andrehora.github.io/testminer/#godotengine/godot`

Explicação: 
Olhando o Godot no TestMiner, o que mais me chamou atenção foi a quantidade de Test Helpers, são 911 arquivos contra 318 arquivos de teste, quase o triplo, e pelas palavras-chave os mais comuns são class, enum, script, local e native. Nas aulas de teste de unidade vimos que o setUp e o tearDown servem para montar a fixture, o estado que o teste precisa, sem repetir esse código em todos os métodos, e eu imagino que o Godot faça algo parecido em escala maior, já que numa engine com 12120 arquivos fonte preparar o cenário para testar física ou parser deve dar bastante trabalho. Só que o TestMiner mostra a quantidade e os termos, não o conteúdo dos arquivos, então isso é uma suposição minha e não dá para afirmar que todos esses helpers são código de setup. Outra coisa que notei foi onde os testes ficam, porque somando tudo que é relacionado a teste são 1245 arquivos, e 984 deles, cerca de 79%, estão na pasta modules, contra 210 na pasta tests, que é só 17%. Isso quer dizer que a maior parte do material de teste fica junto do código que ele valida, e quem mexe num módulo encontra os testes ali mesmo, parecido com a convenção que vimos de dar à classe de teste o nome da classe testada mais o sufixo Test.
Comparando com a pirâmide de testes, o Godot parece seguir a ideia de ter poucos testes e2e, que vimos que são mais lentos, mais caros e mais frágeis, já que o TestMiner mostra só 1 arquivo de E2E, contra 5 de benchmarks, 8 de fixtures e 2 de mocks, display e server, que provavelmente simulam partes pesadas do sistema. Mas isso é uma comparação de arquivos e não de quantidade de testes, então serve mais como indício do que como prova, e o mesmo vale para a proporção entre teste e código de produção, em que os 318 arquivos de teste são cerca de 2,6% dos arquivos fonte, ou uns 10% se contarmos tudo que é relacionado a teste, um número que não diz nada sobre cobertura, porque como vimos na aula, ter muitos arquivos de teste não garante que o código é de fato executado nem que os testes são bons. Por último, as dependências mostram pacotes do nuget como xunit e Microsoft.NET.Test.Sdk, o que combina com o que vimos sobre os frameworks da família xUnit, em que o teste é escrito na mesma linguagem do código testado, então o núcleo do Godot é em C++ mas a parte em C# usa o xUnit, e o projeto acaba combinando mais de uma ferramenta de teste conforme a linguagem.
