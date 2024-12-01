**Atividade para o Projeto Integrador Transdisciplinar em Engenharia de Software II**

**Publish Backend Publish Frontend**

**Resumo do Projeto**

**Objetivo**  
O objetivo desse projeto é dar continuidade ao trabalho feito no PIT I, criando um e-commerce de cupcakes gourmet. A ideia é colocar em prática o que foi desenvolvido até aqui, usando tecnologias modernas para construir tanto o backend quanto o frontend, além de integrar as etapas com CI/CD.

---

### **Funcionalidades**

**Backend**  
- CRUD para Clientes  
- CRUD para Endereço do Cliente  
- Exibir Cupcakes  
- CRUD para Cupcakes  
- Exibir Categorias  
- CRUD para Categorias  
- CRUD para Pedidos  
- Listar Estabelecimentos (baseado no CEP)  
- Relacionamento Estoque x Estabelecimentos  
- Listar Estabelecimentos por área de entrega  

**Frontend**  
- Página inicial com cupcakes e ofertas  
- Exibição de Categorias  
- Exibir cupcakes de uma categoria específica  
- Login (buscar conta por e-mail)  
- Criar novo usuário  
- Auto-completar endereço  
- Cadastro de endereço  
- Visualizar perfil do usuário / logout  
- Carrinho de compras (adicionar, remover itens, limpar, finalizar compra)  
- Listar lojas por região do usuário  
- Exibir pedidos realizados  
- Múltiplos endereços (listar, cadastrar, alterar favorito)  
- Repetir pedidos anteriores  
- Escolher método de pagamento  

---

### **Banco de Dados**

**Escolha do Banco**  
Optamos pelo **PostgreSQL**, pois é fácil de escalar e manter, sendo uma ótima opção para sistemas como esse, que precisam de dados estruturados e relações complexas.

**Modelo de Dados**  
A estrutura de dados foi pensada para ser parecida com sistemas de delivery. Temos:
- **Cliente e Endereço:** Cada cliente pode ter vários endereços (casa, trabalho, etc.).
- **Lojas e Área de Atendimento:** Cada loja tem um alcance de entrega baseado em CEPs, o que facilita a distribuição regional.
- **Cupcakes e Categorias:** Simples e diretas, com informações essenciais para o cliente decidir o que comprar.
- **Pedidos:** Relaciona o cupcake, o endereço e a loja que vai entregar.

**Prisma ORM**  
Escolhemos o Prisma para simplificar o gerenciamento do banco. Ele gera as migrações automaticamente e facilita a manutenção do banco de dados.

---

### **Tecnologias Usadas**

**Backend**  
- **NestJS:** Framework escolhido pela flexibilidade e facilidade de uso. A arquitetura que usamos tem um toque de DDD e Hexagonal, mas de forma mais simplificada, já que queremos serviços pequenos e ágeis.

**Frontend**  
- **Next.js:** Usado no frontend, principalmente pela sua eficiência em renderizar no servidor (SSR) e pelas suas boas práticas de otimização.
- **MVVM:** No frontend, seguimos o padrão MVVM para separar bem a camada visual, a lógica de negócios e as atualizações da interface. Isso ajuda a manter o código organizado e mais fácil de testar.

---

### **Infraestrutura**

**CI/CD**  
- **GitHub Actions e Docker Hub:** Usamos o GitHub Actions para automatizar o processo de integração contínua, criando as builds para o backend e frontend e publicando as imagens no Docker Hub. Apesar da falta de testes automatizados, conseguimos montar uma base de CI eficiente.

**AWS EC2 e S3**  
- **EC2:** Utilizamos uma instância EC2 para rodar os containers Docker com o backend, frontend e banco de dados.  
- **S3:** Usado para armazenar imagens e outros arquivos estáticos que o frontend vai precisar carregar.

**Nginx:** Configuramos o Nginx para atuar como um reverse proxy, ajudando a organizar o tráfego entre os containers Docker e os subdomínios.

---

### **Desafios e Lições**

Durante o desenvolvimento, o maior desafio foi lidar com o Server-Side Rendering (SSR) do Next.js e o roteamento baseado no sistema de arquivos. No começo, a estrutura do Next.js não estava muito clara, mas depois consegui entender melhor como separar as responsabilidades de cada parte (client-side e server-side).

Em relação à arquitetura, a escolha de usar o hexagonal foi interessante, mas decidi simplificar um pouco para facilitar a compreensão e agilidade no desenvolvimento. No fim, conseguimos um código mais direto e funcional.

---

**Conclusão**  
Esse projeto foi um ótimo aprendizado. Apesar de algumas limitações, consegui implementar tudo de forma clara e seguindo boas práticas. O sistema está funcionando e, com o tempo, seria possível melhorar ainda mais a estrutura e adicionar mais funcionalidades.
