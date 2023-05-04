<template>
  
    <CContainer>
      <CRow class="justify-content-center">
        <CCol :md="9" :lg="7" :xl="6">
          <CCard class="mx-4">
            <CCardBody class="p-4">
              <CForm @submit.prevent="submitForm">
                <h4>Create a User</h4>
                <p class="text-medium-emphasis">Create New User Account</p>
                <div  v-if="formValid == false" class="text-danger">{{ empytFieldErrorMSG }}</div>
                <CAlert v-if="emailErrorMSG" color="warning" closeButton>
                  {{emailErrorMSG}}
                </CAlert>
                <CAlert v-if="passwordNotMatchErrorMSG" color="warning" closeButton>
                  {{passwordNotMatchErrorMSG}}
                </CAlert>
                <br/>
                <CInputGroup class="mb-3">
                  <CInputGroupText>
                    <CIcon icon="cil-user" />
                  </CInputGroupText>
                  <CFormInput placeholder="Full Name" autocomplete="fullname" v-model="fullName" />
                </CInputGroup>
                <CInputGroup class="mb-3">
                  <CInputGroupText>@</CInputGroupText>
                  <CFormInput type="email" placeholder="Email" autocomplete="email" v-model="email" />
                </CInputGroup>
                <CInputGroup class="mb-3">
                  <CInputGroupText>
                    <CIcon icon="cil-lock-locked" />
                  </CInputGroupText>
                  <CFormInput
                    type="password"
                    placeholder="Password"
                    autocomplete="new-password"
                    v-model="password"
                  />
                </CInputGroup>
                <CInputGroup class="mb-4">
                  <CInputGroupText>
                    <CIcon icon="cil-lock-locked" />
                  </CInputGroupText>
                  <CFormInput
                    v-model="repeatPassword"
                    type="password"
                    placeholder="Repeat password"
                    autocomplete="new-password"
                  />
                </CInputGroup>
                <div class="d-grid">
                  <CButton color="success" @click="submitForm">Create User</CButton>
                </div>
              </CForm>
            </CCardBody>
          </CCard>
        </CCol>
      </CRow>
    </CContainer>
</template>

<script>

export default {
  name: 'Register',
  data(){
    return {
      fullName: null,
      email: null,
      password: null,
      repeatPassword: null,

      formValid: true,
      empytFieldErrorMSG: null,

      emailErrorMSG: null,
      passwordNotMatchErrorMSG: null,
    }
  },
  methods: {
  submitForm() {
    console.log('submited');
     // reset form validity and clear error messages
    this.formValid = true;
    this.empytFieldErrorMSG = null;
    this.emailErrorMSG = null;
    this.passwordNotMatchErrorMSG = null;

    // Check if required fields are empty
    if (!this.fullName || !this.email || !this.password || !this.repeatPassword) {
      this.formValid = false
      this.empytFieldErrorMSG = "Please fill out all the fields."
      return
    }

    // Check if email is valid
    const emailRegex = /^\S+@\S+\.\S+$/
    if (!emailRegex.test(this.email)) {
      this.emailErrorMSG = "Please enter a valid email address."
      return
    }

    // Check if password and repeat password match
    if (this.password !== this.repeatPassword) {
      this.passwordNotMatchErrorMSG = "Passwords do not match."
      return
    }

    // If all validations pass, submit the form
    alert('Form submitted successfully!')
  }
}

}
</script>
