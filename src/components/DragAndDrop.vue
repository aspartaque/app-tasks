<template>
  <div class="container">
    <div
      class="dropZone"
      @drop="onDrop($event, 1)"
      @dragenter.prevent
      @dragover.prevent
    >
      <div
        v-for="item in getList(1)"
        :key="item.id"
        class="dragEl"
        draggable="true"
        @dragstart="startDrag($event, item)"
      >
        {{ item.title }}
      </div>
    </div>
    <div
      class="dropZone"
      @drop="onDrop($event, 2)"
      @dragenter.prevent
      @dragover.prevent
    >
      <div
        v-for="item in getList(2)"
        :key="item.id"
        class="dragEl"
        draggable="true"
        @dragstart="startDrag($event, item)"
      >
        {{ item.title }}
      </div>
    </div>


  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const items = ref([
      { id: 0, title: 'Item A', list: 1 },
      { id: 1, title: 'Item B', list: 1 },
      { id: 2, title: 'Item C', list: 2 }
    ])

    const getList = (list) => {
      return items.value.filter((item) => item.list == list)
    }

    const startDrag = (event, item) => {
      console.log(item)
      event.dataTransfer.dropEffect = 'move'
      event.dataTransfer.effectAllowed = 'move'
      event.dataTransfer.setData('itemId', item.id)
    }

    const onDrop = (event, list) => {
      const itemId = event.dataTransfer.getData('itemId')
      const item = items.value.find((item) => item.id == itemId)
      item.list = list
    }

    return {
      getList,
      startDrag,
      onDrop
    }
  }
}
</script>

<style>
.dropZone {
  width: 50%;
  margin: 50px auto;
  border: 1px solid #8690cb;
  padding: 10px;
}
.dragEl {
  border: 1px solid #d34666;
  color: #8690cb;
  padding: 5px;
  margin-bottom: 10px;
}
</style>