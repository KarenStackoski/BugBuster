# BugBuster 👾

**Curso:** Ciência da Computação (Unesc)  
**Disciplina:** Realidade Virtual e Aumentada  
**Professor:** Giácomo Antônio Althoff Bolan  
**Desenvolvedora:** Karen Bialescki Stackoski

---

## 📝 Sobre o Jogo & Ambientação
**BugBuster** é um jogo arcade 3D de labirinto com visão superior (*top-down*) e câmera fixa. O projeto traz uma abordagem satírica e bem-humorada sobre a rotina de um **Analista de QA (Quality Assurance / Tester)** correndo contra o tempo para garantir a estabilidade de um sistema antes do temido *deploy*.

O jogador controla o **QA Engineer** dentro de um labirinto que simula os meandros complexos de um código-fonte ou de um servidor de TI. A atmosfera visual adota o estilo *Voxel/Blocos* (inspirado em Minecraft), casando a geometria ortogonal de computação com uma paleta de cores baseada em "Modo Escuro" de IDEs de desenvolvimento.

---

## 🕹️ Regras de Negócio & Mecânicas

* **Objetivo Principal:** Caçar e coletar todos os **Bugs Verdes** espalhados pelo labirinto para validar os casos de teste e liberar o acesso para a próxima fase.
* **Progressão:** O jogo é composto por **3 fases** com labirintos modulares de dificuldades progressivas. A fase é concluída assim que o último Bug Verde do mapa for capturado.
* **Sprint / Corrida Contra o Tempo:** Cada fase inicia com uma contagem regressiva rigorosa de **60 segundos**. O tempo não para!
* **Condições de Game Over:** O jogo é encerrado imediatamente se:
  1. O cronômetro zerar (o prazo do *deploy* estourou).
  2. A barra de vida do personagem chegar a zero (o sistema crashou).
* **Tela de Game Over:** Ao falhar, uma tela preta customizada de *Crash* é exibida, congelando o jogo e permitindo reiniciar a partida ao pressionar a tecla `Enter`.

---

## 📦 Elementos do Jogo (Modelagem Autoral)

Todos os elementos foram modelados no 3ds Max utilizando a técnica de *UVW Unwrap* e mapeamento focado em cores sólidas da paleta do projeto:

1. **Player (QA Engineer):** O herói dos testes, um boneco de blocos equipado com óculos de desenvolvedor.
2. **Bug Verde (Pontos):** Insetos de código que representam falhas corrigidas. Coletá-los soma pontos e é o requisito para avançar de fase.
3. **Bug Vermelho (Dano/Obstáculo):** Bugs críticos em produção. Colidir com eles remove uma fração da vida do Player.
4. **Xícara de Café (Velocidade):** O combustível do desenvolvedor. Coletar o café aumenta temporariamente a velocidade de movimentação do personagem.
5. **Monitor de Computador (Decoração A):** Monitores antigos que compõem o cenário dos corredores.
6. **Elemento de Decoração B:** Adereço temático de escritório de TI posicionado estrategicamente para enriquecer o ambiente do labirinto.
7. **Paredes Modulares (Massa de Código):** Blocos de parede cinza construídos no formato de "Lego" para criar corredores simétricos sem distorcer as texturas.

---

## 📊 Interface do Usuário (UI)
A HUD em tempo real exibe os indicadores essenciais de performance do QA:
* **Pontos:** Contador de Bugs Verdes solucionados.
* **Velocidade:** Velocidade atual de deslocamento do Player.
* **Barra de Vida:** Exibida de forma gráfica através do componente *Slider* da Unity (Estilo Life Bar).
* **Timer Regressivo:** Cronômetro exibindo os segundos restantes para o fim da *Sprint*.

---

## 🔊 Sonorização Adaptativa
O design de áudio foi projetado para gerar imersão e senso de urgência:
* **Músicas por Fase (BGM):** Um total de 4 trilhas sonoras distintas rodando em loop. Cada uma das 3 fases possui uma música exclusiva (ficando mais rápida a cada nível). A quarta trilha é exclusiva para a tela de *Game Over*.
* **Efeitos Sonoros (SFX):** Retornos sonoros (*bips*) emitidos instantaneamente ao coletar itens ou sofrer dano.
* **Mecânica de Pitch por Café:** Sempre que o Player coleta uma xícara de café e aumenta sua velocidade, a propriedade `pitch` do *Audio Source* da música de fundo sofre um acréscimo de `0.1`, acelerando a música e aumentando a adrenalina da gameplay.

---

## ⚙️ Arquitetura Técnica & Organização
O projeto foi desenvolvido visando máxima eficiência e organização:
* **Engine:** Unity
* **IDE:** Microsoft Visual Studio (C#)
* **Modelagem 3D:** 3ds Max (Arquivos `.max` brutos isolados na pasta externa `3D_Models` para manter o repositório limpo; arquivos finais importados em formato `.FBX`).
* **Controle de Versão:** Git + GitHub com arquivo `.gitignore` otimizado para Unity, impedindo o upload de arquivos temporários e caches locais de engine (`Library/`, `Logs/`).
