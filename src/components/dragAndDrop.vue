<template>
  <div class="row px-2">
    <div v-for="category in categories"
         :key="category.id"
         @drop="onDrop($event, category.id)"
         class="droppable col mx-1 py-3"
         @dragover.prevent
         @dragenter.prevent>
      <h2 class="text-center">{{ category.title }}</h2>
      <div v-for="item in items.filter(x => x.categoryId === category.id)"
           @dragstart="onDragStart($event, item)"
           class="draggable "
           draggable="true">
        <p>{{ item.title }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'App',
  setup() {
    const items = ref([
      {
        id: 0,
        title: 'Audi',
        categoryId: 0
      },
      {
        id: 1,
        title: 'BMW',
        categoryId: 1
      },
      {
        id: 2,
        title: 'Cat',
        categoryId: 3
      },
    ]);
    const categories = ref([
      {
        id: 0,
        title: 'Входящие'
      },
      {
        id: 1,
        title: 'На согласовании'
      },
      {
        id: 2,
        title: 'В производстве'
      },
      {
        id: 3,
        title: 'Произведено'
      },
      {
        id: 4,
        title: 'К отгрузке'
      },
    ]);

    function onDragStart(e, item) {
      e.dataTransfer.dropEffect = 'move';
      e.dataTransfer.effectAllowed = 'move';
      e.dataTransfer.setData('itemId', item.id.toString());
    }

    function onDrop(e, categoryId) {
      const itemId = parseInt(e.dataTransfer.getData('itemId'));
      items.value = items.value.map(x => {
        if (x.id === itemId)
          x.categoryId = categoryId;
        return x;
      });
    }

    return {
      items,
      categories,
      onDragStart,
      onDrop
    };
  }
};

</script>

<style lang="scss">
.droppable {
  border-radius: 5px;
  background: rebeccapurple;
  h2{
    font-size: 20px;
    color: white;
  }
}

.draggable {
  background: white;
  padding: 5px;
  border-radius: 5px;
  margin-bottom: 5px;
  p{
    margin: 0;
  }
}

</style>