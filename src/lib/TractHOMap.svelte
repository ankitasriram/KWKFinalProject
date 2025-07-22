<script>
  import { onMount } from "svelte";

  let data = [];
  let error = null;

  onMount(async () => {
    try {
      const response = await fetch(
        "https://api.census.gov/data/2023/acs/acs5/profile?get=NAME,DP04_0046E,DP04_0001E&for=tract:*&in=state:06+county:075"
      );

      const raw = await response.json();

      // Destructure headers + rows
      const [headers, ...rows] = raw;

      data = rows.map(row => {
        const [
          name,
          ownerOccupied,
          totalHousingUnits,
          state,
          county,
          tract,
        ] = row;

        const rate = +ownerOccupied / +totalHousingUnits;

        return {
          name,
          tract,
          rate: isFinite(rate) ? rate : null,
        };
      });
    } catch (err) {
      error = "Failed to fetch Census data.";
      console.error(err);
    }
  });
</script>

{#if error}
  <p>{error}</p>
{:else if data.length === 0}
  <p>Loading data…</p>
{:else}
  <ul>
    {#each data as d}
      <li>
        {d.name}: {(d.rate * 100).toFixed(1)}%
      </li>
    {/each}
  </ul>
{/if}
