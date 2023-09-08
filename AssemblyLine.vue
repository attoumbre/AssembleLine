<template>
    <div>
      TODO -- see src/components/AssemblyLine.vue
      <input data-testid="assembly-add-item" v-model="newItem" @keydown.enter="addItems"/>
      
      <div v-for="(stage,index) in stages" :key="index">
        <div data-testid="assembly-stage">
          {{stage}} 
          
          <button data-testid="assembly-item" v-for="(item, indexItem) in stageItems[index]" 
                  :key="indexItem" @click="goForward(index, indexItem)" 
                  @contextmenu.prevent="goBack(index, indexItem)">
            {{item}}
         </button>
        </div>
        
    </div>
    </div>
  </template>
  
  <script>
  export default {
    props:{
      stages: Array
      
    },
    data(){
      return {
        newItem : '',
        stageItems: this.stages.map(()=>[])
      }
    },
    
    methods:{
      addItems(){
        if(this.newItem){
          this.stageItems[0].unshift(this.newItem)
          this.newItem = ''
        }
      },
      goForward(indexStage, indexItem){
        if(indexStage< this.stages.length - 1){
          const item = this.stageItems[indexStage].splice(indexItem,1)[0]
          this.stageItems[indexStage + 1].unshift(item)
        }else{
          this.stageItems[indexStage].splice(indexItem,1)
        }
      },
      
      goBack(indexStage, indexItem){
        if(indexStage>0){
          const item = this.stageItems[indexStage].splice(indexItem,1)[0]
          this.stageItems[indexStage - 1].push(item)
        }else{
          this.stageItems[indexStage].splice(indexItem, 1)
        }
      }
    }
  }
  </script>
  
  <style>
  </style>