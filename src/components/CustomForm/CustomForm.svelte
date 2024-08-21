<script>
  import { Label, Input, Button, GradientButton } from "flowbite-svelte";
  import { createEventDispatcher, onDestroy } from "svelte";
  import { data1, data2 } from "../../stores/data.store.js";
  import CustomModel from "../CustomModel/CustomModel.svelte";
  import axios from "axios";

  //Form Variables
  let fixed_acidity = 0;
  let volatile_acidity = 0;
  let citric_acid = 0;
  let residual_sugar = 0;
  let chlorides = 0;
  let free_sulfur_dioxide = 0;
  let total_sulfur_dioxide = 0;
  let density = 0;
  let pH = 0;
  let sulphates = 0;
  let alcohol = 0;

  //Loading Variable
  let isLoading = false;
  let spinnerLoading = false;
  let outcomeData;

  //Store Variables
  let test_data_1 = [];
  let test_data_2 = [];

  const dataOneUnsubscribe = data1.subscribe((value) => {
    test_data_1 = [...value];
  });

  const dataTwoUnsubscribe = data2.subscribe((value) => {
    test_data_2 = [...value];
  });

  const dispatch = createEventDispatcher();

  onDestroy(() => {
    dataOneUnsubscribe();
    dataTwoUnsubscribe();
  });

  async function onSubmitForm() {
    isLoading = true;
    let data = {
      formData: [
        fixed_acidity,
        volatile_acidity,
        citric_acid,
        residual_sugar,
        chlorides,
        free_sulfur_dioxide,
        total_sulfur_dioxide,
        density,
        pH,
        sulphates,
        alcohol,
      ],
    };

    try {
      spinnerLoading = true;
      const response = await axios.post(
        "http://localhost:3000/v1/python",
        data
      );
      spinnerLoading = false;
      console.log(response.data);
      outcomeData = response.data.data.data;
      //   console.log(outcomeData.data);
    } catch (err) {
      spinnerLoading = false;
      console.log(err);
    }
    // console.log(data);
    // isLoading = false;
  }

  function testOneClicked() {
    fixed_acidity = test_data_1[0];
    volatile_acidity = test_data_1[1];
    citric_acid = test_data_1[2];
    residual_sugar = test_data_1[3];
    chlorides = test_data_1[4];
    free_sulfur_dioxide = test_data_1[5];
    total_sulfur_dioxide = test_data_1[6];
    density = test_data_1[7];
    pH = test_data_1[8];
    sulphates = test_data_1[9];
    alcohol = test_data_1[10];
  }

  function testTwoClicked() {
    fixed_acidity = test_data_2[0];
    volatile_acidity = test_data_2[1];
    citric_acid = test_data_2[2];
    residual_sugar = test_data_2[3];
    chlorides = test_data_2[4];
    free_sulfur_dioxide = test_data_2[5];
    total_sulfur_dioxide = test_data_2[6];
    density = test_data_2[7];
    pH = test_data_2[8];
    sulphates = test_data_2[9];
    alcohol = test_data_2[10];
  }

  function clearClicked() {
    fixed_acidity = 0;
    volatile_acidity = 0;
    citric_acid = 0;
    residual_sugar = 0;
    chlorides = 0;
    free_sulfur_dioxide = 0;
    total_sulfur_dioxide = 0;
    density = 0;
    pH = 0;
    sulphates = 0;
    alcohol = 0;
  }
</script>

<main>
  {#if isLoading}
    <div class="model">
      <CustomModel
        popupModal={isLoading}
        on:modalCLick={() => {
          isLoading = false;
        }}
        {spinnerLoading}
        outcome={outcomeData}
      />
    </div>
  {/if}

  <div>
    <form on:submit|preventDefault>
      <div class="test-data">
        <button on:click={testOneClicked}>Test-Data-1</button>
        <button on:click={testTwoClicked}>Test-Data-2</button>
        <button on:click={clearClicked}>Clear-All</button>
      </div>

      <div class="grid gap-6 mb-6 md:grid-cols-3">
        <div class="mb-3 text-left">
          <Label for="fixed_acidity" class="block mb-2">Fixed Acidity</Label>
          <Input
            id="fixed_acidity"
            value={fixed_acidity}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
        <div class="mb-3 text-left">
          <Label for="volatile_acidity" class="block mb-2"
            >Volatile Acidity</Label
          >
          <Input
            id="volatile_acidity"
            value={volatile_acidity}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
        <div class="mb-3 text-left">
          <Label for="citric_acid" class="block mb-2">Citric Acid</Label>
          <Input
            id="citric_acid"
            value={citric_acid}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
        <div class="mb-3 text-left">
          <Label for="residual_sugar" class="block mb-2">Residual Sugar</Label>
          <Input
            id="residual_sugar"
            value={residual_sugar}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
        <div class="mb-3 text-left">
          <Label for="chlorides" class="block mb-2">Chlorides</Label>
          <Input
            id="chlorides"
            value={chlorides}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
        <div class="mb-3 text-left">
          <Label for="free_sulfur_dioxide" class="block mb-2"
            >Free Sulfur Dioxide</Label
          >
          <Input
            id="free_sulfur_dioxide"
            value={free_sulfur_dioxide}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
        <div class="mb-3 text-left">
          <Label for="total_sulfur_dioxide" class="block mb-2"
            >Total Sulfur Dioxide</Label
          >
          <Input
            id="total_sulfur_dioxide"
            value={total_sulfur_dioxide}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
        <div class="mb-3 text-left">
          <Label for="density" class="block mb-2">Density</Label>
          <Input
            id="density"
            value={density}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
        <div class="mb-3 text-left">
          <Label for="pH" class="block mb-2">pH</Label>
          <Input id="pH" value={pH} size="sm" placeholder="Enter Value" />
        </div>
        <div class="mb-3 text-left">
          <Label for="sulphates" class="block mb-2">Sulphates</Label>
          <Input
            id="sulphates"
            value={sulphates}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
        <div class="mb-3 text-left">
          <Label for="alcohol" class="block mb-2">Alcohol</Label>
          <Input
            id="alcohol"
            value={alcohol}
            size="sm"
            placeholder="Enter Value"
          />
        </div>
      </div>
      <div class="submit">
        <button type="submit" on:click={onSubmitForm}>
          <GradientButton color="cyanToBlue">Submit!</GradientButton>
        </button>
      </div>
    </form>
  </div>
</main>

<style>
  button {
    margin: 0;
    padding: 0;
    border: 0;
  }

  .submit {
    margin: 7% 0 0% 80%;
    margin-right: -50px;
  }

  .test-data {
    margin-left: 65%;
    margin-bottom: 2%;
  }
</style>
