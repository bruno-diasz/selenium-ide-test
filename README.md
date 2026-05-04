[![Selenium IDE](https://img.shields.io/badge/Selenium_IDE-43B02A?style=for-the-badge&logo=selenium&logoColor=white)](https://www.selenium.dev/selenium-ide/)

Este repositório contém a entrega do Desafio Técnico para a vaga de Estágio em Qualidade de Software (QA). O projeto consiste em uma suíte de testes automatizados de interface (UI) desenvolvida no **Selenium IDE**, com foco na validação de um formulário estruturado (Google Forms).

##  Demonstração e Explicação

Gravei um breve vídeo demonstrando a execução da suíte de testes e explicando a arquitetura e as decisões técnicas tomadas na automação.

**[Link para o video](https://youtu.be/FC9zyFqKoBM)**

---

## Arquitetura e Boas Práticas Adotadas

Durante o desenvolvimento dos scripts, priorizei a aplicação de conceitos fundamentais de Engenharia de Qualidade para garantir testes robustos, manuteníveis e confiáveis:

*   **Padrão de Nomenclatura:** Os Casos de Teste (CTs) foram nomeados seguindo a convenção `[Identificador]_[Ação]_[ComportamentoEsperado]` (ex: `CT01_SubmeterFormulario_ComDadosValidos_DeveEnviarComSucesso`). Isso garante alta rastreabilidade e facilita a leitura de relatórios de falha.
*   **Isolamento de Testes (Independência):** Para evitar "falsos positivos" ou dependência de estado entre os cenários, implementei uma rotina de **Setup** rigorosa. Cada teste inicia com uma nova requisição (`open`) para a URL raiz da aplicação. Isso assegura que o formulário comece com o estado 100% limpo, espelhando o comportamento de um usuário real.
*   **Validação de Estado Dinâmico e Componentes Nativos:** Abordagens específicas foram utilizadas para lidar com o comportamento reativo da interface moderna:
    *   Testes pontuais de validação *on submit* (como formato de e-mail).
    *   Injeção estratégica de eventos JavaScript (`dispatchEvent`) para interagir adequadamente com elementos de *Shadow DOM*, como o `<input type="date">` nativo do HTML5, garantindo que o framework frontend reconhecesse as mudanças de estado feitas pelo Selenium.
*   **Uso de `verify` vs `assert`:** Em testes de validação múltipla (como campos obrigatórios vazios), optei pelo comando `verify text` para permitir que o script valide todas as mensagens de erro na mesma execução (Soft Assert), proporcionando um relatório mais completo sem interromper o teste na primeira falha.

---

## Cobertura de Testes (Casos de Teste)

A suíte cobre tanto o "Caminho Feliz" quanto cenários de exceção e regras de negócio da interface. 

*   ✅ `TC01_DadosValidos_DeveEnviarComSucesso`
*   ❌ `TC02_EmailFormatoInvalido_DeveExibirErro`
*   ❌ `TC03_CartaoComLetras_DeveExibirErro`
*   ❌ `TC04_CamposObrigatoriosEmBranco_DeveExibirErro`

---

## Como executar os testes na sua máquina

Para rodar esta automação localmente, siga os passos abaixo:

1. Instale a extensão do **Selenium IDE** no seu navegador (Chrome ou Firefox).
2. Clone este repositório ou baixe o arquivo com a extensão `.side`.
3. Abra a extensão do Selenium IDE no seu navegador.
4. Clique em **"Open an existing project"** e selecione o arquivo do projeto (`nome-do-seu-arquivo.side`).
5. Clique no botão **"Run all tests"** (ícone de play com três linhas) para executar a suíte completa automaticamente.

---

## Sobre o Autor

Desenvolvido por **Bruno Dias**
Estudante do IFRN e desenvolvedor apaixonado por arquitetura de software e qualidade.

**LinkedIn:** [bruno-diasz](https://br.linkedin.com/in/bruno-diazs)
**Email:** brunoipb1@gmail.com
