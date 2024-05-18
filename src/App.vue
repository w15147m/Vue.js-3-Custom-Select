<template>
  <div>
    <SelectOptions 
      :options="optionss" 
      v-model="parentSelecedOption"
    /> 
    <div class="container mt-5">
      <table class="table table-rounded">
        <thead>
          <tr>
            <th>Name</th>
            <th>Class</th>
            <th>Roll Number</th>
          </tr>
        </thead>
        
        <tbody>
          <tr v-for="(option, index) in filteredOptions" :key="index">
            <td>{{ option }}</td>
            <td>{{ option.class }}</td>
            <td class="text">{{ option.rollNom }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import SelectOptions from './components/SelectOptions.vue';

export default {
  components: {
    SelectOptions
  },
  data() {
    return {
      optionss: [
        "ali" ,
        "mola" ,
        "ali abbas" ,
        "nadeem"
      ],
      parentSelecedOption: ''
    };
  },
  computed: {
    filteredOptions() {
      if (this.parentSelecedOption) {
        return this.optionss.filter(option => option === this.parentSelecedOption);
      } else {
        return this.optionss;
      }
    }
  }
};
</script>

<style>
/* Styling same as before */
</style>
