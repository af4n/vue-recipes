<template>
  <div class="detail">
    <div v-if="recipe"
         class="recipe"
    >
      <h2>{{recipe.title}}</h2>
      <a @click.prevent="toggle"
         href="#"
      >{{visible ? 'Скрыть' : 'Показать'}}</a>
      <p v-if="visible">{{recipe.description}}</p>
      <button @click="$emit('remove', recipe.id)"
              class="btn remove"
      >Удалить</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    recipe: Object
  },
  data() {
    return {
      visible: false
    }
  },
  methods: {
    toggle() {
      this.visible = !this.visible
    }
  },
  watch: {
    recipe() {
      this.visible = false
    }
  }
}
</script>

<style>
  .recipe {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top: 1rem;
    padding-bottom: 1rem;
  }

  .recipe p {
    font-size: .8rem;
    padding-left: 1rem;
    padding-right: 1rem;
    margin-bottom: .5rem;
  }

  .recipe a, .recipe h2 {
    margin-bottom: .5rem;
  }
</style>
