<template>
    <div>
        <button type="button" @click="add()">添加</button>
        <ul>
            <li v-for="(item, index) in lists"
                @click="choose(index)"
                :class="{active: index === current && current !== ''}"
                :key="index">
                ({{ index }}) {{ item }}
            </li>
            current item: {{ current }}
        </ul>
        <button type="button" @click="mov()">移动</button>
        <ul>
            <li v-for="(item, index) in target" :key="index">
               ({{ index }})  {{ item }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  name: 'demo1',
  data () {
    return {
      current: '',
      lists: [100, 200, 300, 400, 500, 600, 700, 800, 900],
      target: []
    }
  },
  methods: {
    choose (index) {
      this.current = index
    },
    mov () {
      if(this.current==='') { return }
      this.target.push(this.lists[this.current])
      this.current = ''
    },
    add () {
      this.lists.push(1000)
    }
  }
}
</script>

<style scoped>
  li.active {background: rgb(152, 186, 236);}
  li { list-style: none;}
</style>