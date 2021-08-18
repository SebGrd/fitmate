<template>
  <div class="parts-list">
    <ul class="parts-list__categories">
      <li v-for="category in categories" :key="`category-${category.id}`"
          class="parts-list__categories__category">
        {{ category.name}}
        <ul class="parts-list__categories__category__parts">
          <li v-for="part in parts.filter((item) => item.category === category.id)"
              :key="part.id"
              class="parts-list__categories__category__parts__part"
              :class="{'parts-list__categories__category__parts__part--active': isSelected(part)}"
              @click="$emit('select-part', part)">
            {{ part.name }}
          </li>
        </ul>
      </li>
    </ul>
  </div>

</template>

<script>
export default {
  name: "BodyPartsList",
  props: {
    selected: {
      type: Array,
      default: () => [],
      deep: true,
    },
  },
  data() {
    return {
      parts: [
        {
          id: 1,
          name: 'Trapezius',
          category: 1,
        },
        {
          id: 2,
          name: 'Lats',
          category: 1,
        },
        {
          id: 3,
          name: 'Biceps',
          category: 2,
        },
        {
          id: 4,
          name: 'Triceps',
          category: 2,
        },
        {
          id: 5,
          name: 'Deltoids',
          category: 2,
        },
        {
          id: 6,
          name: 'Forearms',
          category: 2,
        },
        {
          id: 7,
          name: 'Abs',
          category: 3,
        },
        {
          id: 8,
          name: 'Obliques',
          category: 3,
        },
        {
          id: 9,
          name: 'Pectorals',
          category: 3,
        },
        {
          id: 10,
          name: 'Adductors',
          category: 4,
        },
        {
          id: 11,
          name: 'Quads',
          category: 4,
        },
        {
          id: 12,
          name: 'Hamstrings',
          category: 4,
        },
        {
          id: 13,
          name: 'Calves',
          category: 4,
        },
        {
          id: 14,
          name: 'Glutes',
          category: 4,
        },
      ],
      categories: [
        {
          id: 1,
          name: 'Back',
        },
        {
          id: 2,
          name: 'Arms',
        },
        {
          id: 3,
          name: 'Core',
        },
        {
          id: 4,
          name: 'Legs',
        },
      ],
    };
  },
  methods: {
    isSelected(part) {
      if (this.selected.length === 0) return false;
      return this.selected.some((selectedItem) => selectedItem.id === part.id)
    },
  },
}
</script>

<style scoped lang="scss">
.parts-list{
  &__categories{
    list-style: none;
    padding: 0;
    margin: 0;
    &__category{
      color: var(--primary);
      font-weight: 800;
      &__parts{
        list-style: none;
        padding: 0;
        margin: 0;
        &__part{
          color: black;
          font-weight: 400;
          cursor: pointer;
          padding: 0 .5rem;
          &::selection{
            background: transparent;
          }
          &--active{
            font-weight: 600;
            background: #ebeeee;
            border-left: 2px solid dodgerblue;
          }
        }
      }
    }
  }
}
</style>