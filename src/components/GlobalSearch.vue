<template>
  <article class="global-search">
    <form class="global-search-form" @submit.prevent="processSearch">
      <label>
        <i class="material-icons global-search-form__icon">work</i>
        <input
          class="global-search-form__text"
          type="text"
          placeholder="Title, companies, expertise or benefits"
          v-model="searchQuery"
        />
      </label>
      <button
        class="global-search-form__button"
        type="button"
        @click="processSearch"
      >
        Search
      </button>
    </form>
  </article>
</template>

<script>
import store from "@/store";

export default {
  name: "GlobalSearch",
  data: function() {
    return {
      searchQuery: ""
    };
  },
  methods: {
    processSearch() {
      store.dispatch("job/fetchJobs", {
        params: {
          search: this.searchQuery
        }
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.global-search {
  background: transparent url("../assets/images/backgroundImg.png") center
    no-repeat;
  background-size: cover;
  display: flex;
  justify-content: center;

  &-form {
    background: #fff;
    padding: 4px;
    margin: 42px 0;
    border-radius: 4px;
    display: flex;
    box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.1);

    label {
      display: flex;
      align-items: center;
    }

    &__icon {
      margin: 15px 9.5px 18px 12px;
      color: #b9bdcf;
      font-size: 0.9375em;
    }

    &__text {
      width: 600px;
      margin-right: 9.5px;
      margin-bottom: 3px;
      border: none;
      outline: none;
      font-size: 0.85em;
      color: #b9bdcf;

      &::placeholder {
        color: #b9bdcf;
      }
    }

    @media (max-width: 860px) {
      &__text {
        width: 400px;
      }
    }

    @media (max-width: 650px) {
      &__text {
        width: 300px;
      }
    }

    @media (max-width: 550px) {
      & {
        flex-direction: column;
      }
      &__text {
        width: 220px;
      }
    }

    &__button {
      background: #1e86ff;
      color: #fff;
      border: none;
      outline: none;
      padding: 14px 48px;
      border-radius: 4px;
      font-weight: 500;
    }
  }
}
</style>
