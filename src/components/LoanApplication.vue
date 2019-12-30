<template>
  <section>
    <mdb-row>
      <mdb-col md="12">
        <mdb-card cascade narrow class="mt-5 mb-5">
          <mdb-view class="gradient-card-header blue darken-2">
            <h4 class="h4-responsive text-white">Loan Application</h4>
          </mdb-view>
          <mdb-container class="mb-5">
            <!-- Custom styles -->
            <h2 class="my-5"></h2>
            <form class="needs-validation" novalidate @submit="submitForm">
              <!-- Product Type -->
              <div class="form-row">
                <div class="col-md-12 mb-4">
                  <label for="cbType" style="font-weight: bold"
                    >Product Type</label
                  >
                  <br />
                  <div
                    class="custom-control custom-radio custom-control-inline"
                  >
                    <input
                      type="radio"
                      class="custom-control-input"
                      id="cbTypePO"
                      name="cbType"
                      v-model="type"
                      v-bind:value="'typePO'"
                      checked
                      required
                    />
                    <label class="custom-control-label" for="cbTypePO"
                      >Purchase Order</label
                    >
                  </div>

                  <div
                    class="custom-control custom-radio custom-control-inline"
                  >
                    <input
                      type="radio"
                      class="custom-control-input"
                      id="cbTypeIF"
                      name="cbType"
                      v-model="type"
                      v-bind:value="'typeIF'"
                      required
                    />
                    <label class="custom-control-label" for="cbTypeIF"
                      >Invoice Financing</label
                    >
                  </div>
                  <div class="valid-feedback">Looks good!</div>
                </div>
              </div>

              <div class="form-row">
                <div class="col-md-6 mb-4">
                  <!-- Loan Amount -->
                  <label for="tbAmount" style="font-weight: bold"
                    >Loan Amount</label
                  >
                  <br />
                  <input
                    type="number"
                    class="form-control"
                    id="tbAmount"
                    placeholder="0"
                    min="0"
                    v-model="amount"
                    outline
                    required
                  />
                  <div class="valid-feedback">Looks good!</div>
                  <div class="invalid-feedback">Amount is not valid</div>
                </div>
              </div>

              <div class="form-row">
                <div class="col-md-6 mb-4">
                  <!-- Interest Rate -->
                  <label for="cbInterest" style="font-weight: bold" class="mb-2"
                    >Interest Rate (based on product type chosen)</label
                  >
                  <br />
                  <div
                    class="custom-control custom-radio custom-control-inline"
                  >
                    <input
                      type="radio"
                      class="custom-control-input"
                      id="cbInterest15"
                      name="cbInterest"
                      v-bind:checked="type == 'typePO'"
                      disabled
                    />
                    <label class="custom-control-label" for="cbInterest15"
                      >1.5%</label
                    >
                  </div>

                  <div
                    class="custom-control custom-radio custom-control-inline"
                  >
                    <input
                      type="radio"
                      class="custom-control-input"
                      id="cbInterest18"
                      name="cbInterest"
                      v-bind:checked="type == 'typeIF'"
                      disabled
                    />

                    <label class="custom-control-label" for="cbInterest18"
                      >1.8%</label
                    >
                  </div>
                </div>
              </div>

              <div class="form-row">
                <div class="col-md-6 mb-4">
                  <!-- Terms -->
                  <label for="cbTerms" style="font-weight: bold" class="mb-2"
                    >Terms (months)</label
                  >
                  <br />
                  <div
                    class="custom-control custom-radio custom-control-inline"
                  >
                    <input
                      type="radio"
                      class="custom-control-input"
                      id="cbTerms3"
                      name="cbTerms"
                      checked
                      required
                    />
                    <label class="custom-control-label" for="cbTerms3">3</label>
                  </div>

                  <div
                    class="custom-control custom-radio custom-control-inline"
                  >
                    <input
                      type="radio"
                      class="custom-control-input"
                      id="cbTerms6"
                      name="cbTerms"
                      required
                    />
                    <label class="custom-control-label" for="cbTerms6">6</label>
                  </div>

                  <div
                    class="custom-control custom-radio custom-control-inline"
                  >
                    <input
                      type="radio"
                      class="custom-control-input"
                      id="cbTerms12"
                      name="cbTerms"
                      required
                    />
                    <label class="custom-control-label" for="cbTerms12"
                      >12</label
                    >
                  </div>

                  <div
                    class="custom-control custom-radio custom-control-inline"
                  >
                    <input
                      type="radio"
                      class="custom-control-input"
                      id="cbTerms24"
                      name="cbTerms"
                      required
                    />
                    <label class="custom-control-label" for="cbTerms24"
                      >24</label
                    >
                  </div>
                </div>
              </div>

              <div class="form-row">
                <div class="col-md-6 mb-4">
                  <!-- Documents -->
                  <label style="font-weight: bold" class="mb-2"
                    >Documents</label
                  >
                  <br />
                  <div class="custom-file">
                    <input
                      type="file"
                      class="custom-file-input"
                      id="upload"
                      required
                    />
                    <label class="custom-file-label" for="upload"
                      >Choose file...</label
                    >
                    <div class="invalid-feedback">A document is required</div>
                  </div>
                </div>
              </div>

              <mdb-btn color="primary" type="submit">Submit form</mdb-btn>
            </form>
          </mdb-container>
        </mdb-card>
      </mdb-col>
    </mdb-row>
  </section>
</template>

<script>
import {
  mdbRow,
  mdbCol,
  mdbCard,
  mdbCardBody,
  mdbView,
  mdbMask,
  mdbCardTitle,
  mdbCardText,
  mdbCardFooter,
  mdbContainer,
  mdbIcon,
  mdbBtn,
  mdbPagination,
  mdbPageNav,
  mdbPageItem
} from 'mdbvue'
import Vue from 'vue'
import $ from 'jquery'
import loading from 'vue-loading-overlay'
import 'vue-loading-overlay/dist/vue-loading.css'

Vue.use(loading)

export default {
  name: 'LoanApplication',
  components: {
    mdbRow,
    mdbCol,
    mdbCard,
    mdbCardBody,
    mdbView,
    mdbMask,
    mdbCardTitle,
    mdbCardText,
    mdbCardFooter,
    mdbContainer,
    mdbIcon,
    mdbBtn,
    mdbPagination,
    mdbPageNav,
    mdbPageItem,
    loading
  },
  data() {
    return {
      type: 'typePO',
      amount: 0,
      interest: 1.5,
      terms: 3,
      documents: '',
      fullPage: false
    }
  },
  mounted() {
    $('input[type="file"]').change(function(e) {
      var fileName = e.target.files[0].name
      $('.custom-file-label').html(fileName)
      this.documents = fileName
    })
  },
  methods: {
    submitForm(event) {
      event.preventDefault()
      event.target.classList.add('was-validated')
      this.displayLoader()
      // AXIOS -> MySQL
    },
    displayLoader() {
      let loader = this.$loading.show({
        color: '#4285F4',
        backgroundColor: 'bdbdbd',
        loader: 'dots',
        container: this.fullPage ? null : this.$refs.formContainer,
        canCancel: true,
        onCancel: this.onCancel
      })
      setTimeout(() => {
        loader.hide()
      }, 5000)
    },
    onCancel() {
      console.log('User cancelled the loader.')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card.card-cascade .view.gradient-card-header {
  padding: 1rem 1rem;
  text-align: center;
}
.card.card-cascade h3,
.card.card-cascade h4 {
  margin-bottom: 0;
}
</style>
