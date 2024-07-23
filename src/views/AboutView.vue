<template>
  <div class="container mt-4">
    <h1 class="text-center mb-4">Sobre o Projeto</h1>

    <section class="mb-5">
      <h2>Tecnologias e Ferramentas Utilizadas</h2>
      <ul>
        <li>
          <strong><a href="https://vuejs.org/" target="_blank" rel="noopener noreferrer">Vue.js</a></strong>: Um framework progressivo para a construção de interfaces de usuário e aplicativos de página única (SPA). A abordagem reativa e baseada em componentes facilita o desenvolvimento de interfaces complexas.
        </li>
        <li>
          <strong><a href="https://vitejs.dev/" target="_blank" rel="noopener noreferrer">Vite</a></strong>: Utilizado como o bundler de desenvolvimento, Vite proporciona um ambiente de desenvolvimento rápido e moderno com suporte a Hot Module Replacement (HMR) e uma experiência de build otimizada.
        </li>
        <li>
          <strong><a href="https://getbootstrap.com/" target="_blank" rel="noopener noreferrer">Bootstrap 5</a></strong>: Framework CSS utilizado para o design e a responsividade, oferecendo um conjunto robusto de ferramentas para criar layouts responsivos e estilizados rapidamente.
        </li>
        <li>
          <strong><a href="https://pokeapi.co/" target="_blank" rel="noopener noreferrer">PokeAPI</a></strong>: A API integrada que fornece dados detalhados sobre Pokémon, incluindo atributos, habilidades e estatísticas base.
        </li>
      </ul>
    </section>

    <section class="mb-5">
      <h2>Funcionalidades do Projeto</h2>
      <ul>
        <li><strong>Busca pelo nome ou id do Pokémon:</strong> Permite aos usuários pesquisar determinado pokemon.</li>
        <li><strong>Visualização Detalhada:</strong> Exibe detalhes completos de um Pokémon selecionado, incluindo imagem, XP, altura, peso, tipos, habilidades e estatísticas base.</li>
        <li><strong>Paginação:</strong> A lista de Pokémon é paginada para melhorar a navegação e a usabilidade, exibindo um número controlado de Pokémon por página.</li>
        <li><strong>Design Responsivo:</strong> A interface é totalmente responsiva, garantindo uma ótima experiência de usuário em dispositivos móveis e desktop.</li>
      </ul>
    </section>

    <section>
      <h2>Conclusão</h2>
      <p>
        Este projeto demonstra a integração eficaz de Vue.js e Bootstrap com a PokeAPI, oferecendo uma aplicação rica em funcionalidades e visualmente atraente para todos os fãs de Pokémon. A combinação dessas tecnologias proporciona uma experiência de usuário fluida e interativa, tornando o desenvolvimento e a manutenção do projeto muito mais gerenciáveis.
      </p>

    </section>
  </div>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 0 1rem;
  margin-bottom: 100px; 
}

h1 {
  font-size: 2rem;
  margin-bottom: 1rem;
}

h2 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

p {
  font-size: 1rem;
  line-height: 1.6;
}

ul {
  list-style-type: disc;
  padding-left: 1.5rem;

  li {
    margin-bottom: 0.5rem;
  }
}

a {
  color: #007bff;
  text-decoration: none;

  &:hover {
    text-decoration: underline;
  }
}

@media (max-width: 576px) {
  h1 {
    font-size: 1.5rem;
  }

  h2 {
    font-size: 1.25rem;
  }
  
  p {
    font-size: 0.875rem;
  }
}
</style>


