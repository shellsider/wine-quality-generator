<script>
  import CustomForm from "./components/CustomForm/CustomForm.svelte";
</script>

<main id="main">

  <!-- Title-Section -->
  <section id="title">
    <div class="five">
      <h1>
        Wine Quality Prediction
        <span>Example Tagline Text</span>
      </h1>
    </div>
  </section>

  <!-- FormSection -->
  <section id="form" class="container">
    <div class="image-container">
      <img
        src="src\assets\Premium Photo _ Red wine pouring in a glass from a bottle.jpg"
        alt="Wine_image"
      />
    </div>
    <div class="form-container">
      <CustomForm />
    </div>
  </section>
</main>

<style>
  #main {
    width: 100%;
  }

  :global(body) {
    /* margin-top: 73px; */
    position: relative;
    background-image: url("src/assets/fireplace.jpg");
    background-size: cover; /* Cover the entire background */
    background-position: center; /* Center the background image */
    background-attachment: fixed; /* Fixed background position */
    background-color: rgba(0, 0, 0, 0.5); /* 50% less transparent */
    z-index: -2;
  }

  :global(body)::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.7);
    z-index: -1;
  }

  /* Title Styling */
  h1 {
    position: relative;
    padding: 0;
    margin: 0;
    font-family: "Raleway", sans-serif;
    font-weight: 300;
    font-size: 40px;
    color: #ffffff;
    -webkit-transition: all 0.4s ease 0s;
    -o-transition: all 0.4s ease 0s;
    transition: all 0.4s ease 0s;
  }

  h1 span {
    display: block;
    font-size: 0.5em;
    line-height: 1.3;
  }
  h1 em {
    font-style: normal;
    font-weight: 600;
  }

  .five h1 {
    text-align: center;
    font-size: 22px;
    font-weight: 700;
    color: #ffffff;
    text-transform: uppercase;
    word-spacing: 1px;
    letter-spacing: 2px;
  }
  .five h1 span {
    margin-top: 40px;
    text-transform: none;
    font-size: 0.75em;
    font-weight: normal;
    font-style: italic;
    font-family: "Playfair Display", "Bookman", serif;
    color: #ffffff;
    letter-spacing: -0.005em;
    word-spacing: 1px;
    letter-spacing: none;
  }
  .five h1:before {
    position: absolute;
    left: 0;
    bottom: 38px;
    width: 60px;
    height: 4px;
    content: "";
    left: 50%;
    margin-left: -30px;
    background-color: #dfdfdf;
  }
  /* Title StylingEnd */

  /* Form-Sectio-Style-Start */

  #form {
    margin-top: 30px;
    background: linear-gradient(rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.1)),
      url("src/assets/fireplace.jpg"); /* Your image as the background */
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
  }

  .container {
    display: flex;
  }

  .image-container {
    width: 30%;
    border-radius: 10px;
    background-color: #4d4d4d; /* Darker background color */
    overflow: hidden;
  }

  .image-container img {
    width: 100%;
    height: auto;
  }

  .form-container {
    width: 70%;
    padding: 3% 5% 0 5%; /* Add padding to make the form more readable */
    background-color: rgba(
      255,
      255,
      255,
      0.5
    ); /* Lighter background color with transparency */
    border-radius: 10px; /* Match the image container's border radius */
    pointer-events: auto; /* Enable pointer events for the form container */
  }
  /* Form-Sectio-Style-End */
</style>
