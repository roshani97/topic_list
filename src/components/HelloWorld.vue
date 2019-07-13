<template>
  <div id="hello">
  
   <div id="navi1">
     <b-navbar  type="dark" variant="dark" >
    <b-navbar-nav  class="w-100  mb-1" >
      <b-navbar-brand href="#">Welcome</b-navbar-brand>

          </b-navbar-nav>
      <b-navbar-nav>
      <b-nav-item href="#" class="pl-5 mb-1" >Subjects</b-nav-item>
      <b-nav-item href="#" class="pl-5 mb-1">Topics</b-nav-item>
      <b-nav-item href="#" class="pl-5 mb-1">Questions</b-nav-item>

      <!-- Navbar dropdowns -->
      <b-nav-item-dropdown text="Utilities" class="pl-5 mb-1">
        <b-dropdown-item href="#">list1</b-dropdown-item>
        <b-dropdown-item href="#">list2</b-dropdown-item>
        <b-dropdown-item href="#">list3</b-dropdown-item>
        <b-dropdown-item href="#">list</b-dropdown-item>
      </b-nav-item-dropdown>

      <b-nav-item-dropdown text="Page" class="pl-5 mb-1">
          <b-dropdown-item href="#">p1</b-dropdown-item>
          <b-dropdown-item href="#">p2</b-dropdown-item>
          <b-dropdown-item href="#">p3</b-dropdown-item>
          <b-dropdown-item href="#">p4</b-dropdown-item>
        </b-nav-item-dropdown>

      <b-nav-item href="#" class="pl-5 mb-1">Table</b-nav-item>
      <b-nav-item href="#" class="pl-5 mb-1">Chart</b-nav-item>
      <b-nav-item href="#" class="pl-5 mb-1">Logout</b-nav-item>
    </b-navbar-nav>
  </b-navbar>
  
  </div>
  <div id="navi2">
  <div>
  <b-navbar type="light" variant="light">
    <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-nav-form>
  </b-navbar>
</div>
  </div>

  <div id="sub_list" align="right" class="p-5 mb-1">
    <b-button v-b-modal.modal-1 variant="success">Add Topic</b-button>
    <b-modal id="modal-1" title="ADD TOPIC DETAILS" hide-footer>
    <table>
    <tr><td>Topic ID</td><td><input type="text" v-model="tid"></td></tr>
    <tr><td>Subject Name</td><td><input type="text" v-model="tname" ></td></tr>
    <tr><td><button @click="addTableRow()">ADD TOPIC</button></td></tr>
    
    </table>
  </b-modal>
  <b-button  @click="deleteTableRow()" variant="danger">Remove</b-button>

<br>
<h3 align="center" style="color:#001a06">Topic List</h3>
<table  class="table table-striped " striped id="sub_id">
<thead style="background:#b8b894">
<th>Topic ID</th>
<th>Topic Name</th>
<th>Action</th>
<th>Remove Topic</th>

</thead>
<tr v-for="item in topic_detail" :key="item.tid">
  
  <td>{{ item.tid}}</td>
  <td>{{ item.tname}}</td>
  
<td><b-button v-b-modal.modal-2>Edit</b-button>
    <b-modal id="modal-2" title="EDIT TOPIC DETAILS">
    <table>
    <tr><td>Topic ID</td><td><input type="text" v-model="tid"></td></tr>
    <tr><td>Topic Name</td><td><input type="text" v-model="tname" ></td></tr>
    </table>
  </b-modal></td>
  
 <td><b-form-checkbox checked="check_value='true"></b-form-checkbox></td>
  
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
            this.topic_detail.pop();
    }
	}

}
</script>
<style scoped>
#sub_list{
  padding:10px;
}
</style>

