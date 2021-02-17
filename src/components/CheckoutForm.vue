<template>
  <div id="checkout-form">
    <h4 class="mb-3">Billing address</h4>
    <form class="needs-validation">
      <div class="row">
        <div class="col-md-6 mb-3">
          <label for="firstName">
            First name
            <span class="text-danger">*</span>
          </label>
          <input
            v-model="first_name"
            type="text"
            class="form-control"
            id="firstName"
            placeholder
            value
            required
          />
          <div class="invalid-feedback">Valid first name is required.</div>
        </div>
        <div class="col-md-6 mb-3">
          <label for="lastName">
            Last name
            <span class="text-danger">*</span>
          </label>
          <input
            v-model="last_name"
            type="text"
            class="form-control"
            id="lastName"
            placeholder
            value
            required
          />
          <div class="invalid-feedback">Valid last name is required.</div>
        </div>
      </div>

      <div class="mb-3">
        <label for="email">
          Email
          <span class="text-danger">*</span>
        </label>
        <input
          v-model="email"
          type="email"
          class="form-control"
          id="email"
          placeholder="you@example.com"
        />
        <div class="invalid-feedback">Please enter a valid email address for shipping updates.</div>
      </div>

      <div class="mb-3">
        <label for="phone">
          Phone Number
          <span class="text-danger">*</span>
        </label>
        <input
          v-model.number="phone"
          type="number"
          class="form-control"
          id="phonenumber"
          placeholder
        />
        <div class="invalid-feedback">Please enter a valid Phone Number for shipping updates.</div>
      </div>

      <div class="mb-3">
        <label for="address">
          Address
          <span class="text-danger">*</span>
        </label>
        <input
          v-model="address_1"
          type="text"
          class="form-control"
          id="address"
          placeholder="1234 Main St"
          required
        />
        <div class="invalid-feedback">Please enter your shipping address.</div>
      </div>

      <div class="mb-3">
        <label for="address2">
          Address 2
          <span class="text-muted">(Optional)</span>
        </label>
        <input
          v-model="address_2"
          type="text"
          class="form-control"
          id="address2"
          placeholder="Apartment or suite"
        />
      </div>

      <div class="row">
        <div class="col-md-5 mb-3">
          <label for="country">
            Country
            <span class="text-danger">*</span>
          </label>
          <select v-model="country" class="custom-select d-block w-100" id="country" required>
            <option value>Choose...</option>
            <option>United States</option>
          </select>
          <div class="invalid-feedback">Please select a valid country.</div>
        </div>
        <div class="col-md-4 mb-3">
          <label for="state">
            State
            <span class="text-danger">*</span>
          </label>
          <select v-model="state" class="custom-select d-block w-100" id="state" required>
            <option value>Choose...</option>
            <option>California</option>
          </select>
          <div class="invalid-feedback">Please provide a valid state.</div>
        </div>
        <div class="col-md-3 mb-3">
          <label for="zip">Zip</label>
          <input v-model="zip" type="text" class="form-control" id="zip" placeholder required />
          <div class="invalid-feedback">Zip code required.</div>
        </div>
      </div>
      <!-- <hr class="mb-4" />
      <div class="custom-control custom-checkbox">
        <input type="checkbox" class="custom-control-input" id="same-address" />
        <label
          class="custom-control-label"
          for="same-address"
        >Shipping address is the same as my billing address</label>
      </div>
      <div class="custom-control custom-checkbox">
        <input type="checkbox" class="custom-control-input" id="save-info" />
        <label class="custom-control-label" for="save-info">Save this information for next time</label>
      </div>
      <hr class="mb-4" />

      <h4 class="mb-3">Payment</h4>-->

      <!-- <div class="d-block my-3">
        <div class="custom-control custom-radio">
          <input
            id="credit"
            name="paymentMethod"
            type="radio"
            class="custom-control-input"
            checked
            required
          />
          <label class="custom-control-label" for="credit">Credit card</label>
        </div>
        <div class="custom-control custom-radio">
          <input id="debit" name="paymentMethod" type="radio" class="custom-control-input" required />
          <label class="custom-control-label" for="debit">Debit card</label>
        </div>
        <div class="custom-control custom-radio">
          <input
            id="paypal"
            name="paymentMethod"
            type="radio"
            class="custom-control-input"
            required
          />
          <label class="custom-control-label" for="paypal">PayPal</label>
        </div>
      </div>
      <div class="row">
        <div class="col-md-6 mb-3">
          <label for="cc-name">Name on card</label>
          <input type="text" class="form-control" id="cc-name" placeholder required />
          <small class="text-muted">Full name as displayed on card</small>
          <div class="invalid-feedback">Name on card is required</div>
        </div>
        <div class="col-md-6 mb-3">
          <label for="cc-number">Credit card number</label>
          <input type="text" class="form-control" id="cc-number" placeholder required />
          <div class="invalid-feedback">Credit card number is required</div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-3 mb-3">
          <label for="cc-expiration">Expiration</label>
          <input type="text" class="form-control" id="cc-expiration" placeholder required />
          <div class="invalid-feedback">Expiration date required</div>
        </div>
        <div class="col-md-3 mb-3">
          <label for="cc-cvv">CVV</label>
          <input type="text" class="form-control" id="cc-cvv" placeholder required />
          <div class="invalid-feedback">Security code required</div>
        </div>
      </div>
      <hr class="mb-4" />-->
      <button
        @click="submit()"
        type="button"
        class="btn btn-primary btn-lg btn-block mb-5"
      >Continue to checkout</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "CheckoutForm",

  data() {
    return {
      first_name: null,
      last_name: null,
      email: null,
      phone: null,
      address_1: null,
      address_2: null,
      country: null,
      state: null,
      zip: null,
    };
  },

  methods: {
    submit() {},
  },
};
</script>

