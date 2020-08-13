<template>
  <div class="tree" :id="'check'+ data.parentid">
        <input type="checkbox" v-model="data.checked" :id="data.id" @change="checkboxParent(data.checked, data.parentid, data.id)">     
        <label :for="data.id">{{data.name}}</label>

        <div class="test" v-if="data.children && data.children.length">
            <tree v-for="child in data.children" :data="child" :key="child.id"></tree>
        </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'

@Component
export default class tree extends Vue {
    @Prop(Object)  data!: any
    checkboxParent(status: boolean, parent: number, currentId: number){
        if (parent != 0){
            this.checkboxChild(parent, currentId)
        }
        this.data.children.forEach( (item: any, i: number, arr: any) => {
            if (status) {
                item.checked = true
            } else {item.checked = false}
        })
    }
    checkboxChild(parent: number, currentId: number){
        let elementsBlock: any = document.querySelectorAll('#check' + parent)
        let parentEl: HTMLInputElement = document.getElementById(parent.toString())
        
        let checkedElements: number = 0
        for (let i = 0; elementsBlock.length > i; i++){
            const element = elementsBlock[i].childNodes[0]
            if (element.checked){
                checkedElements++
            }
        }
        if (elementsBlock.length != checkedElements && checkedElements > 0){
            parentEl.indeterminate = true
        } else if (checkedElements = checkedElements){
            parentEl.indeterminate = false
            parentEl.checked = true
        } else if (checkedElements == 0){
            parentEl.indeterminate = false
            parentEl.checked = false
        } 
        
    }
}
</script>


<style lang="sass" scoped>   
.tree
    text-align: left 
.test
    margin-left: 55px
    text-align: left
</style>