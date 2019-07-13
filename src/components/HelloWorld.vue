<template>
  <div id="hello">
  
  <div id="sub_list" align="right" class="p-5 mb-1">
    <b-button v-b-modal.modal-1 variant="success">Add Topic</b-button>
    <b-modal id="modal-1" title="ADD TOPIC DETAILS" hide-footer>
    <table>
    <tr><td>Topic ID</td><td><input type="text" v-model="tid"></td></tr>
    <tr><td>Subject Name</td><td><input type="text" v-model="tname" ></td></tr>
    <tr><td><button @click="addTableRow()">ADD TOPIC</button></td></tr>
    
    </table>
  </b-modal>
<br>
<h3 align="center" style="color:#001a06">Topic List</h3>
<table  class="table table-striped " striped id="sub_id">
<thead style="background:#b8b894">
<th></th>
<th>Topic ID</th>
<th>Topic Name</th>
<th>Action</th>
<th>Remove Topic</th>

</thead>
<tr v-for="item in topic_detail" :key="item.tid">
  <td><b-form-checkbox checked="check_value='true"></b-form-checkbox></td>
  <td>{{ item.tid}}</td>
  <td>{{ item.tname}}</td>
  
<td><b-button v-b-modal.modal-2>Edit</b-button>
    <b-modal id="modal-2" title="EDIT TOPIC DETAILS">
    <table>
    <tr><td>Topic ID</td><td><input type="text" v-model="tid"></td></tr>
    <tr><td>Topic Name</td><td><input type="text" v-model="tname" ></td></tr>
    </table>
  </b-modal></td>
  <td><b-button  @click="deleteTableRow()" variant="danger">Remove</b-button></td>
 
  
</tr>
</table>
</div>
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
         tid:'',
         tname:'',
         topic_detail:[],
         row_len:'0',

    }
  },
  methods:{
    addTableRow: function () { 
       var my_object = {
        tid:this.tid,
        tname:this.tname
      };
      this.topic_detail.push(my_object);
      this.$bvModal.hide('modal-1');
   },
    deleteTableRow: function() { 
            alert("hiii");
    }
	}

}
</script>
<style scoped>
#sub_list{
  padding:10px;
}
</style>

