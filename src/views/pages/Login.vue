<template>
<div class="bg-light min-vh-100 d-flex flex-row align-items-center">
    <CContainer>
        <CRow class="justify-content-center">
            <CCol :md="8">
                <CCardGroup>
                    <CCard class="p-4">
                        <CCardBody>
                            <CForm @submit.prevent="submitForm">
                                <h1>Login</h1>
                                <p class="text-medium-emphasis">Sign In to your account</p>
                                <CInputGroup class="mb-3">
                                    <CInputGroupText>
                                        <CIcon icon="cil-user" />
                                    </CInputGroupText>
                                    <CFormInput type="email" placeholder="Email" autocomplete="email" inputmode="email" v-model="email" :class="{'is-invalid': emailError}" />
                                    <div v-if="emailError" class="invalid-feedback">{{ emailError }}</div>
                                </CInputGroup>
                                <CInputGroup class="mb-4">
                                    <CInputGroupText>
                                        <CIcon icon="cil-lock-locked" />
                                    </CInputGroupText>
                                    <CFormInput type="password" placeholder="Password" autocomplete="current-password" v-model="password" :class="{'is-invalid': passwordError}" />
                                    <div v-if="passwordError" class="invalid-feedback">{{ passwordError }}</div>
                                </CInputGroup>
                                <CRow>
                                    <CCol :xs="6">
                                        <CButton @click="submitForm" color="primary" class="px-4"> Login </CButton>
                                    </CCol>
                                    <CCol :xs="6" class="text-right">
                                        <CButton color="link" class="px-0">
                                            Forgot password?
                                        </CButton>
                                    </CCol>
                                </CRow>
                            </CForm>
                        </CCardBody>
                    </CCard>
                    <CCard class="text-white bg-primary py-5" style="width: 44%">
                        <CCardBody class="text-center">
                            <div>
                                <h2>Welcome</h2>
                                <p>
                                    Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                                    sed do eiusmod tempor incididunt ut labore et dolore magna
                                    aliqua.
                                </p>
                                <CButton color="light" variant="outline" class="mt-3">
                                    Button
                                </CButton>
                            </div>
                        </CCardBody>
                    </CCard>
                </CCardGroup>
            </CCol>
        </CRow>
    </CContainer>
</div>
</template>

<script>
export default {
    name: 'Login',
    data() {
    return {
      email: '',
      password: '',
      emailError: null,
      passwordError: null
    }
  },
  methods: {
    submitForm() {
      this.emailError = null
      this.passwordError = null
      if (!this.email.match(/^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/)) {
        this.emailError = 'Please enter a valid email like username@gmail.com'
      }
      if (!this.password) {
        this.passwordError = 'Please enter a valid password'
      }
      if (this.email && this.password) {
        // perform login logic
        console.log(this.email, this.password);
      }
    }
  }
}
</script>
