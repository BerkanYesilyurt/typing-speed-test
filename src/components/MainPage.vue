<template>
    <div class="container py-4">
      <header class="pb-3 mb-4 border-bottom">
        <a href="/" class="d-flex align-items-center text-dark text-decoration-none">
          <span class="fs-4">Typing Speed Test</span>
        </a>
      </header>

      <div class="p-5 mb-4 bg-body-tertiary rounded-3">
        <center>
        <div class="card">
          <div class="card-body">
              <div class="container-fluid py-5">
                <h1 class="display-5 fw-bold">Test your typing skills!</h1>
                <p class="col-md-8 fs-4">Want to know how to improve your typing speed? The first step to learn to type fast and increase your typing speed is to take a timed typing test!</p>

                <div class="row g-0 text-center p-2 mb-4" style="background-color: #ced4da">
                  <div class="col-sm-6 col-md-12 display-6">Keywords</div>
                </div>

                <input class="form-control form-control-lg mb-4" type="text" placeholder=".form-control-lg" aria-label=".form-control-lg example">
              </div>
          </div>
        </div>
        </center>
      </div>

      <div class="row align-items-md-stretch">
        <div class="col-md-6">
          <div class="h-100 p-5 text-bg-dark rounded-3">
            <h2>Change the background</h2>
            <p>Swap the background-color utility and add a `.text-*` color utility to mix up the jumbotron look. Then, mix and match with additional component themes and more.</p>
            <button class="btn btn-outline-light" type="button">Example button</button>
          </div>
        </div>
        <div class="col-md-6">
          <div class="h-100 p-5 bg-body-tertiary border rounded-3">
            <h2>Add borders</h2>
            <p>Or, keep it light and add a border for some added definition to the boundaries of your content. Be sure to look under the hood at the source HTML here as we've adjusted the alignment and sizing of both column's content for equal-height.</p>
            <button class="btn btn-outline-secondary" type="button">Example button</button>
          </div>
        </div>
      </div>

      <footer class="pt-3 mt-4 text-body-secondary border-top">
        &copy; 2023
      </footer>
    </div>
</template>

<script>
export default {
  name: 'MainPage'
}
</script>

<style scoped>

</style>
