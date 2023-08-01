<template>
<div class="table-box ">

    <table class="table">
      <thead>
        <tr>
          <th scope="col">Sr#</th>
          <th scope="col">Name</th>
          <th scope="col">RoomVIP</th> 
          <th scope="col">Boxes</th>
          <th scope="col">FamilySeats</th> 
          <th scope="col">TotalSeats</th>
          <th scope="col">EngineerName</th> 
          <th scope="col">Color</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(data, index) in trainsStore.allTrainsObject.data" :key="index" :class="{ 'gray': index % 2 === 0}">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ data.name }}</td>
          <td>{{ data.roomVIP }}</td> 
          <td>{{ data.boxes }}</td>
          <td>{{ data.familySeats }}</td>
          <td>{{ data.totalSeats }}</td>
          <td >{{ data.engineerDetail[0].name }}</td>
          <td>{{ data.color }}</td>
        </tr>
  
      </tbody>
    </table>
    </div>
  </template>
  
  <script setup>
  import { useTrainsStore } from '../../stores/Trains/Tranins';
  import router from '../../router/index'
  
  /////////// updated train function
  function updatetrain(id) {
    router.push('/dashboard/updatetrain/'+id)
  }
  /////////// see one train function
  function OneTrainDetail(id) {
    router.push('/dashboard/seeonetrain/' + id)
  }
  
  const trainsStore = useTrainsStore();
  /////////// delete train function
   function deleteTrain(id) {
    trainsStore.deleteTrainAction(id)
  }
  
  trainsStore.getTrainsAction()


  
  </script>
  <style scoped>
  .table-box{
  padding: 1rem auto;
  border: 1px solid rgb(191, 191, 191);
  border-radius: 8px;
  overflow-x: scroll;
  /* cursor:url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'  width='40' height='48' viewport='0 0 100 100' style='fill:black;font-size:24px;'><text y='50%'>🚀</text></svg>") 16 0,auto;  */
}
  button{
    border-radius: 5px;
    border: none;
    padding: .7rem 1.5rem;
  }
  .gray{
  background-color: rgb(59 196 126 / 16%);
}
</style>