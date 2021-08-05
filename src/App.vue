<template>
  <div id="app" class="container mt-4  bg-light rounded p-4">
    <h2 class="text-center">Vue Form</h2>
    <div class="row justify-content-evenly">

      <div class="col-md-5">
  
        <div class="mb-3">
          <label for="email" class="form-label">Email</label>
          <input type="email" class="form-control" id="email" placeholder="name@example.com" v-model.lazy="userData.email">
        </div>
        <div class="mb-3">
          <label for="password" class="form-label">Password</label>
          <input type="password" class="form-control" id="password" v-model.lazy="userData.password">
        </div>
        <div class="mb-3">
          <label for="age" class="form-label">Age</label>
          <input type="number" class="form-control" id="age" v-model.lazy="userData.age">
        </div>
        <div class="mb-3">
          <label for="message" class="form-label">Message</label>
          <textarea class="form-control" id="message" rows="3" v-model.lazy="message"></textarea>
        </div>

        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="sendMail" id="sendMail" v-model="sendMail">
          <label class="form-check-label" for="sendMail">
            Send Mail
          </label>
        </div>
        <div class="form-check mb-3">
          <input class="form-check-input" type="checkbox" value="sendInfomail" id="sendInfoMail" v-model="sendMail">
          <label class="form-check-label" for="sendInfoMail">
            Send Infomail
          </label>
        </div>

        <div class="form-check">
          <input class="form-check-input" type="radio" name="gender" id="male" value="Male" v-model="gender">
          <label class="form-check-label" for="male">
            Male
          </label>
        </div>
        <div class="form-check mb-3">
          <input class="form-check-input" type="radio" name="gender" id="female" value="Female" v-model="gender">
          <label class="form-check-label" for="female">
            Female
          </label>
        </div>
        <div class="mb-3">
          <label for="priority" class="form-label fw-bold">Priority</label>
          <select class="form-select" aria-label="Priority" id="priority" v-model="selectedPriority">
            <!-- <option selected>Open this select menu</option> -->
            <option v-for="(priority, index) in priorities" :key="index">{{ priority }}</option>
          </select>
        </div>
        <button class="btn btn-primary" @click.prevent="submitted">Submit</button>
      </div>
      <div class="col-md-5" v-if="isSubmitted">
        <div class="card">
          <div class="card-header">
            <h4>Info of form</h4>
          </div>
          <div class="card-body">
            <p>Email: {{ userData.email }}</p>
            <p>Password: {{ userData.password }}</p>
            <p>Age: {{ userData.age }}</p>
            <p style="white-space: pre">Message: {{ message }}</p>
            <p class="fw-bold">Send mail? </p>
            <ul>
              <li v-for="(item, index) in sendMail" :key="index">{{ item }}</li>
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
        age: '',
      },
        message: '',
        sendMail: [],
        gender: '',
        selectedPriority: 'High',
        priorities: ['High', 'Medium', 'Low'],
        isSubmitted: false
    }
  },
  methods: {
    submitted(){
      this.isSubmitted = true;
    }
  }
}
</script>
