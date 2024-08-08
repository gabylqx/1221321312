

<template>
  <div>
	  <el-button @click="test">test</el-button>
	  
	  <el-card
	    v-for="(list1, index) in list"
	    :key="index"
	    style="width: 80%; margin-left: 20px; min-height: 80px"
	  >
	    组:{{ list1.name }}
	    <br />
	    <VueDraggable
	      class="flex flex-col gap-2 p-4 w-300px h-300px m-auto bg-gray-500/5 rounded overflow-auto"
	      v-model="list[index].children"
	      style="width: 100%; min-height: 80px"
	      animation="150"
	      ghostClass="ghost"
	      group="people"
	      @update="onUpdate"
	      @add="onAdd"
	      @remove="remove"
	    >
	      <el-card
	        v-for="item in list[index].children"
	        :key="item.id"
	        class="cursor-move h-30 bg-gray-500/5 rounded p-3"
	      >
	        {{ item.name }}
	      </el-card>
	    </VueDraggable>
	  </el-card>
  </div>
</template>

<script>
import ElementUI from 'element-ui';
import { VueDraggable } from 'vue-draggable-plus';
export default {
  name: 'JsCoursewareMeta',
  components: {
    VueDraggable,
  },
  data() {
    return {
      list: [
		  {
			id:1,
			name:"23",
			children:[
				{
					id:1,
					name:"23",
					children:[
						
					]
				}
			]
		  },{
			id:1,
			name:"23",
			children:[
				{
					id:1,
					name:"23",
					children:[
						
					]
				}
			]
		  }
	  ],
      // 搜索
      searchForm: {
        id: '',
        metaId: '',
        tagId: '',
        coursewareId: 1,
      },
      createForm: {
        coursewareId: 2,
        sort: null,
      },
    };
  },
  created() {
	  
  },
  methods: {
    onUpdate() {
      console.log('update');
    },
    onAdd() {
      console.log('add');
    },
    remove() {
      console.log('remove');
    },
    test() {
      console.log(JSON.stringify(this.list));
    },
  },
};
</script>
