<svelte:options customElement="custom-table" />

<script>
  import { TabulatorFull as Tabulator } from "tabulator-tables";
  import { onMount } from "svelte";

  let {
    data = [
      { id: 1, a: 1, b: 1 },
      { id: 2, a: 2, b: 2 },
      { id: 3, a: 3, b: 3 },
    ],
    columns = [
      { field: "id", title: "ID" },
      { field: "a", title: "A" },
      { field: "b", title: "B" },
    ],
  } = $props();

  let tableComponent;

  onMount(() => {
    new Tabulator(tableComponent, {
      data: data, //link data to table
      reactiveData: true, //enable data reactivity
      columns: columns, //define table columns
      layout: "fitDataTable",
    });
  });
</script>

// tabulator fails if we don't wrap with outer div
<div>
  <div bind:this={tableComponent}></div>
</div>

<svelte:head>
  <link
    href="https://unpkg.com/tabulator-tables@4.9.1/dist/css/tabulator.min.css"
    rel="stylesheet"
  />
</svelte:head>
