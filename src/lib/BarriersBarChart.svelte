<script>
    import Highcharts from "highcharts";
    import Chart from "@highcharts/svelte";

    export let title = "Bar Chart";
    export let categories = [];
    export let series = [];

    $: options = {
        chart: { type: "column" },
        title: { text: null },
        xAxis: { categories },
        yAxis: {
            min: 0,
            title: { text: "Count / Rate" },
        },
        tooltip: { shared: true },
        plotOptions: { column: { pointPadding: 0.2, borderWidth: 0 } },
        legend: { enabled: false },
        series,
    };
</script>

<Chart {options} highcharts={Highcharts} />
