# ☕ Framework de Validação de Dados — Java

## 📌 Sobre o projeto

Projeto desenvolvido em Java com o objetivo de implementar um mini-framework de validação de dados utilizando recursos da linguagem para verificar automaticamente atributos de objetos e aplicar regras específicas de negócio.

A aplicação utiliza **anotações personalizadas (Annotations)** e **Reflection** para identificar campos que precisam ser validados, tornando o processo de validação mais organizado, reutilizável e flexível.

O projeto utiliza como exemplo contas bancárias de pessoas físicas e jurídicas, aplicando diferentes critérios de validação conforme o tipo de conta.

## 🎯 Objetivo

Desenvolver um mecanismo de validação capaz de:

- Verificar campos obrigatórios.
- Validar limites de tamanho de atributos.
- Verificar valores positivos.
- Aplicar regras específicas para pessoas físicas e jurídicas.
- Identificar e registrar violações encontradas durante a validação.
- Retornar resultados estruturados indicando se um objeto é válido ou inválido.

## 🛠️ Tecnologias e recursos utilizados

- **Java 25:** linguagem utilizada no desenvolvimento.
- **Maven:** gerenciamento e execução do projeto.
- **JUnit 5:** criação e execução dos testes automatizados.
- **AssertJ:** biblioteca para facilitar as verificações nos testes.
- **Java Reflection:** inspeção dos atributos e leitura de anotações em tempo de execução.
- **Annotations:** criação de anotações personalizadas para definir critérios de validação.
- **Records:** representação de dados de forma concisa.
- **Sealed Classes/Interfaces:** organização dos possíveis resultados de validação.

## ⚙️ Funcionalidades e conceitos implementados

### 1. Anotações personalizadas

Foram criadas três anotações para definir critérios de validação:

- `@NaoNulo`: identifica atributos que não podem receber valores nulos.
- `@Positivo`: verifica se um valor deve ser maior que zero.
- `@Tamanho`: estabelece limites mínimos e máximos para o tamanho de um atributo.

### 2. Validação por Reflection

A classe `Validador` utiliza Reflection para examinar os atributos dos objetos e identificar as anotações aplicadas.

Dessa forma, as regras de validação podem ser executadas dinamicamente, sem precisar implementar manualmente uma verificação individual para cada atributo.

### 3. Regras de negócio

O framework contempla regras específicas para cada modalidade de conta:

**Pessoa Física (PF):**
- Verificação da idade mínima de 18 anos.
- Validação dos campos e informações cadastrais.

**Pessoa Jurídica (PJ):**
- Verificação do capital social mínimo de R$ 10.000,00.
- Validação dos campos e informações cadastrais.

### 4. Resultado da validação

Os resultados são organizados por meio da interface `ResultadoValidacao`, com duas possibilidades:

- `Valido`: indica que nenhuma violação foi encontrada.
- `Invalido`: apresenta a lista de violações identificadas.

A estrutura `Violacao` registra o campo que apresentou problema e a respectiva mensagem.

## 📂 Estrutura do projeto

```text
atividade1/
│
├── pom.xml
├── mvnw
├── mvnw.cmd
│
└── src/
    ├── main/
    │   └── java/
    │       └── br/edu/utfpr/
    │           │
    │           ├── Main.java
    │           │
    │           ├── anotacoes/
    │           │   ├── NaoNulo.java
    │           │   ├── Positivo.java
    │           │   └── Tamanho.java
    │           │
    │           ├── dominio/
    │           │   ├── ContaBancaria.java
    │           │   ├── ContaPessoaFisica.java
    │           │   └── ContaPessoaJuridica.java
    │           │
    │           └── validacao/
    │               ├── ResultadoValidacao.java
    │               ├── Validador.java
    │               └── Violacao.java
    │
    └── test/
        └── java/
            └── br/edu/utfpr/validacao/
                └── ValidadorTest.java
```

## 🧪 Testes automatizados

O projeto possui testes utilizando JUnit 5 e AssertJ para verificar diferentes situações de validação.

Entre os cenários contemplados estão:

1. Pessoa física com dados válidos.
2. Pessoa física menor de idade.
3. Pessoa física com campos inválidos.
4. Pessoa jurídica com dados válidos.
5. Pessoa jurídica com capital social insuficiente.
6. Envio de objeto nulo para validação.
7. Pessoa física com data de nascimento nula.
8. Pessoa jurídica com capital social nulo.

## ▶️ Como executar

O projeto utiliza Maven Wrapper, dispensando a necessidade de instalar o Maven manualmente.

**Executar os testes:**

```bash
./mvnw test
```

No Windows, utilizando PowerShell:

```powershell
.\mvnw.cmd test
```

**Compilar e executar a aplicação:**

```bash
.\mvnw.cmd compile exec:java
```

## 📚 Conhecimentos desenvolvidos

Este projeto permite praticar conceitos importantes da programação Java:

- Programação orientada a objetos (POO).
- Criação e utilização de anotações personalizadas.
- Java Reflection.
- Inspeção de atributos em tempo de execução.
- Encapsulamento e organização em pacotes.
- Records.
- Interfaces e estruturas de resultados.
- Sealed Classes e Pattern Matching.
- Tratamento de valores nulos.
- Testes automatizados com JUnit 5.
- Asserções com AssertJ.
- Gerenciamento de dependências com Maven.

## 💡 Considerações finais

O desenvolvimento deste projeto proporciona uma aplicação prática de recursos avançados do Java, demonstrando como anotações e Reflection podem ser combinados para construir mecanismos reutilizáveis de validação.

A proposta também permite compreender como separar regras técnicas de validação das regras específicas de negócio, favorecendo a organização, a manutenção e a reutilização do código.

---

**Projeto acadêmico desenvolvido durante os estudos de Java II — Pós-graduação.**
