<template>

  <div class="array">
    <div v-for="item in finishedArray" :key="item.id">
      <tree :data="item"></tree>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';
import tree from './tree.vue';

@Component({
  components: {
    tree,
  },
})
export default class treeOuter extends Vue {
  @Prop(Array)  array!: any
  
  message: string = 'Hello!'
  finishedArray: Array<object> = []

  mounted () { 
    this.finishedArray = this.unflatten(this.array);
  }

  unflatten(arr: Array<Object>) {
        let tree = [],
        mappedElement: any = {},
        arrElem: any,
        mappedElem;

    for (let i = 0; arr.length > i; i++) {
      arrElem = arr[i];
      mappedElement[arrElem.id] = arrElem;
      mappedElement[arrElem.id]['children'] = [];
    }

    for (const id in mappedElement) {
      if (mappedElement.hasOwnProperty(id)) {
        mappedElem = mappedElement[id];
        if (mappedElem.parentid) {
          mappedElement[mappedElem['parentid']]['children'].push(mappedElem);
        }
        else {
          tree.push(mappedElem);
        }
      }
    }
    return tree;
  }

}
</script>

<style scoped lang="sass">
h3
  margin: 40px 0 0
.array
  padding: 40px

  
</style>
