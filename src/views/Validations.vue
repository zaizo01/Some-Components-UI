<template>
  <div class="mt-5">
      <h1>Validations</h1>
      <form @submit.prevent="submitInfo">
      <input type="email" 
             placeholder="Enter your email..." 
             class="form-control my-3"
             v-model.lazy="$v.email.$model"
             :class="{'is-invalid': $v.email.$error}">
      <small v-if="!$v.email.required" class="text-danger">Required</small>
      <small v-if="!$v.email.email" class="text-danger">Email Incorrecto</small>
      <small></small>
      <!-- <p>{{$v.email}}</p> -->

      <input type="password" 
      placeholder="Password..."
      class="form-control"
      v-model="$v.passOne.$model"
      :class="{'is-invalid': $v.passOne.$error}">
      <small class="text-danger" v-if="!$v.passOne.minLength">Min 6 characteres</small>
      <!-- <p>{{$v.passOne}}</p> -->

      <input type="password" 
      placeholder="Repeat Password..."
      class="form-control"
      v-model="$v.passTwo.$model"
      :class="{'is-invalid': $v.passTwo.$error}">
      <small class="text-danger" v-if="!$v.passTwo.sameAsPassword">PassWord are not same</small>
      <!-- <p>{{$v.passTwo}}</p> -->
      <button class="btn btn-primary mt-3"
            :disabled="$v.$invalid">Send</button>
      <p>{{$v.$invalid}}</p>
    </form>
  </div>
</template>

<script>
import { required, sameAs, email, minLength, between } from 'vuelidate/lib/validators'
export default {
    name: 'Validations',
    data() {
        return {
            email: '',
            passOne: '',
            passTwo: ''
        }
    },
    validations: {
        email: {
            required,
            email
        },
        passOne: {
            required,
            minLength: minLength(6)
        },
        passTwo: {
            sameAsPassword: sameAs('passOne')
        }
    },
    methods: {
        submitInfo(){
        console.log('submit!')
        this.$v.$touch()
        if (this.$v.$invalid) {
           console.log('ERROR');
        } else {
           console.log('All Good');
        }
        }
    },
}
</script>
