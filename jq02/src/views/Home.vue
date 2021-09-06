<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    
  
    <b-container align-v="center">
  <b-row>

<job-card v-for="job in displayjobs" :key="job.id" :name="job.name"></job-card>

</b-row>
     <b-pagination
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      first-text="First"
      prev-text="Prev"
      next-text="Next"
      last-text="Last"
      @input="paginate(currentPage)"
    ></b-pagination>

<!-- <job-card></job-card>
<job-card></job-card>
<job-card></job-card> -->

    <!-- <b-col md="3">
      <b-card title="This is card" 
      img-src="http://picsum.photos/600/300/?image=25"
      img-alt="job-info"
      img-top
      tag="article"
      style="max-width:20rem"
      class="mb-2">
        <b-card-text>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Aperiam veniam ipsa temporibus tenetur asperiores eaque mollitia eum natus repellat nulla hic magnam vel, voluptates quam nostrum consequatur reiciendis officia libero.

        </b-card-text>
        <b-button variant="primery">Apply</b-button>
      </b-card>
    </b-col>

    <b-col md="3">
      <b-card title="This is card" 
      img-src="http://picsum.photos/600/300/?image=25"
      img-alt="job-info"
      img-top
      tag="article"
      style="max-width:20rem"
      class="mb-2">
        <b-card-text>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Aperiam veniam ipsa temporibus tenetur asperiores eaque mollitia eum natus repellat nulla hic magnam vel, voluptates quam nostrum consequatur reiciendis officia libero.

        </b-card-text>
        <b-button variant="primery">Apply</b-button>
      </b-card>
    </b-col>

<b-col md="3">
      <b-card title="This is card" 
      img-src="http://picsum.photos/600/300/?image=25"
      img-alt="job-info"
      img-top
      tag="article"
      style="max-width:20rem"
      class="mb-2">
        <b-card-text>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Aperiam veniam ipsa temporibus tenetur asperiores eaque mollitia eum natus repellat nulla hic magnam vel, voluptates quam nostrum consequatur reiciendis officia libero.

        </b-card-text>
        <b-button variant="primery">Apply</b-button>
      </b-card>
    </b-col>

<b-col md="3">
      <b-card title="This is card" 
      img-src="http://picsum.photos/600/300/?image=25"
      img-alt="job-info"
      img-top
      tag="article"
      style="max-width:20rem"
      class="mb-2">
        <b-card-text>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Aperiam veniam ipsa temporibus tenetur asperiores eaque mollitia eum natus repellat nulla hic magnam vel, voluptates quam nostrum consequatur reiciendis officia libero.

        </b-card-text>
        <b-button variant="primery">Apply</b-button>
      </b-card>
    </b-col> -->


  
</b-container>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import JobCard from "@/components/JobCard.vue";


export default {
  name: "Home",
  components: {"job-card": JobCard}
,
mounted(){
  this.fetchData();
},
data(){
  return{
    jobs :[],
    displayjobs : [],
    currentPage:1,
    rows:1,
    perPage :3
  };
},
methods :{ 
  
async fetchData(){
const res =await fetch("jobs.json");
const val = await res.json();   
this.jobs=val; 
this.displayjobs=val.slice(0,3)
this.rows=this.jobs.length;
console.log(val);
},
paginate(currentPage){
  // alert(currentPage)

  const start = (currentPage-1) * this.perPage;
  this.displayjobs=this.jobs.slice(start,start+3);
  
}}
};

</script>
