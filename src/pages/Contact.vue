<template>
  <div>
      <h1 class="heading_Lg margin_md text-center">Feel Free to Contact Me</h1>

      <b-row class="text-center margin_sm">
        <b-col cols="4">
          <h3>Email: cjaygonzales117@gmail.com</h3>
        </b-col>

        <b-col cols="4">
          <h3 col-4>(+353) 83 828 6822</h3>
        </b-col>

        <b-col cols="4">
          <h3>Co.Dublin, Ireland</h3>
        </b-col>
      </b-row>
      

      <b-form class="margin_md">
        <label for="text-password">Name</label>
        <b-form-input type="password" id="text-password" aria-describedby="password-help-block"></b-form-input>
      </b-form>

      <b-form class="margin_sm">
        <label for="text-password">Email</label>
        <b-form-input type="password" id="text-password" aria-describedby="password-help-block"></b-form-input>
      </b-form>

      <b-form class="margin_sm">
        <label for="text-password">Message</label>
        <b-form-textarea type="password" id="text-password" aria-describedby="password-help-block"></b-form-textarea>
      </b-form>
      <b-button class="submit_button margin_sm ">Submit</b-button>



  </div>
</template>

<script>


export default {
  name: 'Contact'
}
</script>

<style>


.center{
  justify-content: center;
}

.submit_button{
  width: 100%;
  height: 100px;
  border-radius: 0;
  font-size: 32px;
}

.heading_contact{
  font-size: 32px;
}

.heading_Lg{
  font-size: 64px;
}

.margin_sm{
  margin-top: 10px;
}

.margin_md{
  margin-top: 60px;
}

.margin_lg{
  margin-top: 100px;
}
</style>