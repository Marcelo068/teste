## 1. Estrutura Geral
A estrutura segue uma abordagem modular, onde diferentes funcionalidades e componentes são isolados em seus próprios diretórios. Isso facilita a manutenção e escalabilidade do projeto.

## 2. Diretórios e Arquivos Principais
- assets/img: Armazena imagens e ícones utilizados na aplicação. Isso centraliza todos os recursos visuais, facilitando o gerenciamento e a troca de assets, se necessário.

- components: Contém subdiretórios para cada componente principal (Map, Search, SideBar), cada um com seus respectivos arquivos de estilo (.module.css) e implementação (.tsx). Isso promove a separação de responsabilidades, onde cada componente gerencia seu próprio escopo de funcionalidades e estilos.

-  Map: Provavelmente responsável por exibir o mapa e as posições dos equipamentos.
-  Search: Gerencia a funcionalidade de busca, permitindo ao usuário filtrar equipamentos.
-  SideBar: Exibe a lista de equipamentos, seus estados e histórico, com integração de dropdowns.
- data: Armazena arquivos JSON com dados estáticos ou simulados, como equipment.json, equipmentModel.json, etc. Esses arquivos são úteis para desenvolvimento local, testes, ou para servir como mock data antes de integrar uma API real.

- services: Contém a lógica de negócios e funções utilitárias. A separação de interfaces (interfaces) em um subdiretório ajuda a manter uma tipagem clara e a separação de preocupações entre contratos (interfaces) e implementação (MapService.ts).

- store: Gerencia o estado global da aplicação com Redux. O arquivo equipmentSlice.ts define o slice de estado relacionado ao equipamento, enquanto index.ts provavelmente configura a store Redux. Essa centralização do estado permite que diferentes componentes compartilhem e acessem dados globais.

- Arquivos de configuração e root:

App.tsx e App.css: Componentes e estilos principais da aplicação.
index.tsx e index.css: Ponto de entrada da aplicação, onde o React DOM é renderizado.
Testes (App.test.tsx, setupTests.ts): Configurações e testes para garantir a qualidade e o funcionamento da aplicação.
reportWebVitals.ts: Utilizado para medir a performance da aplicação.
## 3. Uso do Redux
- O Redux é usado para gerenciar estados globais, como o equipamento selecionado (selectedEquipmentId) e a consulta de pesquisa (searchQuery). Isso permite uma melhor coordenação entre componentes, garantindo que eles tenham acesso às mesmas fontes de verdade e possam reagir a mudanças de estado global de forma consistente.

- A decisão de usar Redux é especialmente relevante em aplicações onde múltiplos componentes precisam acessar ou modificar o mesmo estado global. Aqui, o equipmentSlice.ts encapsula a lógica de estado do equipamento, simplificando o gerenciamento e atualização do estado de forma previsível.

## 4. Estilos Modulares
- A escolha por módulos CSS (.module.css) em cada componente permite a aplicação de estilos scoped, prevenindo conflitos de CSS e garantindo que os estilos sejam aplicados apenas ao componente correspondente. Isso é particularmente útil em aplicações maiores, onde o risco de conflitos de estilos é maior.
## 5. Decisões Técnicas
- Modularidade: Cada componente e serviço foi isolado em seu próprio módulo, facilitando a manutenção e a escalabilidade. Isso também promove o reuso de componentes e serviços em diferentes partes da aplicação.

- Separação de Responsabilidades: A lógica de negócios está separada da lógica de exibição, o que segue boas práticas de desenvolvimento de software e facilita testes e manutenção.

- Mock Data: Armazenar os dados em JSON facilita o desenvolvimento local e testes, permitindo iterar rapidamente sem depender de uma API externa.