<template>
  <div class="container">
    <form>
      <div class="row">
        <div class="col-xs-12 col-sm8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <h1>File a Complaint</h1>
            <hr>
            <div class="form-group">
              <label for="email">Mail:</label>
              <input type="text" id="email" class="form-control" v-model="userData.email">
            </div>

            <div class="form-group">
              <label for="password">Password:</label>
              <input type="password" id="password" class="form-control" v-model="userData.password">
            </div>

             <div class="form-group">
              <label for="age">Age:</label>
              <input type="number" id="age" class="form-control" v-model="userData.age">
            </div>
        </div>
      </div>

      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <label for="message">Message</label>
          <textarea id="message" row="5" class="form-control" v-model="message"></textarea>
        </div>
      </div>

       <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <div class="form-group">
            <label for="sendmail">
              <input type="checkbox" id="sendmail" value="SendMail" v-model="sendMail">Send Mail
            </label>
            <label for="sendInfomail">
              <input type="checkbox" id="sendInfomail" value="SendInfoMail" v-model="sendMail">Send Infomail
            </label>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <div class="form-group">
            <label for="male">
              <input type="radio" id="male" value="Male" v-model="gender">Male
            </label>
            <label for="female">
              <input type="radio" id="female" value="Female" v-model="gender">Female
            </label>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <div class="form-group">
            <label for="priority">Priority</label>
              <select id="priority" class="form-control" v-model="selectedPriority">
                <option v-for="priority in priorities"> {{ priority }}</option>
              </select>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <div class="form-group">
            <button type="submit" class="btn btn-primary" v-on:click.prevent="submitted">Submit</button>
          </div>
        </div>
      </div>


    </form>
    <hr>
    <div class="row" v-if="isSubmitted">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h4>You data</h4>
          </div>
          <div class="panel-body">
            <p>Mail: {{ userData.email }}</p>
            <p>Password: {{ userData.password }}</p>
            <p>Age: {{ userData.age }}</p>
            <p style="white-space: pre">Message: {{ message }}</p>
            <p><strong>Send Mail?</strong></p>
            <ul>
              <li v-for="item in sendMail"> {{ item }}</li>
            </ul>
            <p>Gender: {{ gender }}</p>
            <p>Priority: {{ selectedPriority }}</p>
          </div>

        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      userData: {
        email: '',
        password: '',
        age: 36
      },
      message: '',
      sendMail: [],
      gender: 'Male',
      priorities: ['High','Medium','Low'],
      selectedPriority: 'Low',
      isSubmitted: false
    }
  },
  methods: {
    submitted() {
      this.isSubmitted = true;
    }
  }
}
</script>

<style lang="scss">
</style>
