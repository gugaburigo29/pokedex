<template>
  <div class="tags" :class="[direction, size]">
    <div v-for="type in types" class="tag" :key="random + type">{{type}}</div>
  </div>
</template>

<script>
    export default {
        name: "PokemonTags",
        props: {
            types: {required: true},
            direction: {default: ''},
            size: {default: 'sm'}
        },
        computed: {
            random() {
                return Math.random() * 100;
            }
        }
    }
</script>

<style lang="scss" scoped>
  @import "../style/mixins";

  .tags {
    display: flex;
    flex-direction: column;
    align-items: start;
  }

  .tag {
    font-size: 12px;
    padding: .2em .4em;
    background-color: rgba(255, 255, 255, .25);
    margin-bottom: 5px;
    border-radius: 5px;
  }

  .row {
    flex-direction: row;

    .tag {
      margin-right: 5px;
    }
  }

  .column {
    flex-direction: column;
  }

  .sm {
    .tag {
      @include mediaMaxWidth(400px) {
        font-size: 10px;
      }
    }
  }

  .md {
    .tag {
      font-size: 14px;
      padding: .2em 1.2em;
      border-radius: 25px;
      @include mobile_old {
        font-size: 12px;
      }
    }
  }
</style>
