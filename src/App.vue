<template lang="html">
  <div id="app" class="container">
    <div class="page-header">
      <h1>กรอกข้อมูล</h1>
    </div>
    <form id="form" class="form-inline">
    <div class="form-group">
      <input type="text" id="nameSubject" class="form-control" placeholder="ชื่อวิชา" v-model="temp.nameSubject">
    </div>
    <div class="form-group">
      <input type="text" id="credit" class="form-control" placeholder="หน่วยกิต"  maxlength="3" v-model="temp.credit">
    </div>
    <div class="form-group">
      <input type="text" id="grade" class="form-control" placeholder="เกรด"  maxlength="3" v-model="temp.grade">
    </div>
    <input v-on:click="addterm" :disabled="temp.nameSubject == '' || temp.credit == '' || temp.grade == ''" type="submit" class="btn btn-default" value="+ Add">
  </form>
    <div class="page-header">
      <h1>คำนวณเกรด</h1>
    </div>
    <div class="">
      <table class="table table">
      <thead>
        <tr>
        <th>
          #
        </th>
        <th>
          ชื่อวิชา
        </th>
        <th>
          หน่วยกิต
        </th>
        <th>
          เกรด
        </th>
        <th>
          Delete
        </th>
      </tr>
    </thead>
      <tbody>
        <tr  v-for="(terms, index) in term">
          <td>
            {{index + 1}}
          </td>
          <td>
            {{terms.nameSubject}}
          </td>
          <td>
            {{terms.credit}}
          </td>
          <td>
            {{terms.grade}}
          </td>
          <td>
            <input type="submit" class="btn btn-primary" value="Delete" v-on:click="remove(book)">
          </td>
        </tr>
      </tbody>
    </table>
    </div>

  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      temp: {
        nameSubject: '',
        credit: '',
        grade: ''
      },
      term: []
    }
  },
  methods: {
    addterm: function () {
      let vm = this
      vm.term.push(this.temp)
      this.temp.nameSubject = ''
      this.temp.credit = ''
      this.temp.grade = ''
      console.log(this.temp)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
