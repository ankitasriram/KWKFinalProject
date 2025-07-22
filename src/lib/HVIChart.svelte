<script>
    import Highcharts from "highcharts";
    import Chart from "@highcharts/svelte";

    const counties = [
        "Sonoma",
        "Napa",
        "San Francisco",
        "Santa Clara",
        "Contra Costa",
        "Alameda",
        "Marin",
        "Solano",
        "San Mateo",
    ];

    // Placeholder data — replace with your actual values
    const blackRatios = [
        8.537297297, 4.361435304, 28.03332687, 14.80447221, 10.10480381,
        15.49553151, 19.32285498, 8.057332039, 15.68435141,
    ];
    const whiteRatios = [
        7.289022623, 7.600726145, 8.172626109, 8.845150284, 6.10388488,
        7.646731434, 9.268077827, 5.716441845, 9.109249282,
    ];

    const chartOptions = {
        chart: { type: "bar" },
        title: {
            text: "Home Value to Income Ratio by Race - White vs Black (2023)",
            style: { fontSize: "20px" },
        },
        xAxis: {
            categories: counties,
            crosshair: true,
            title: { text: "Bay Area Counties" },
        },
        yAxis: {
            min: 0,
            title: { text: "Home Value ÷ Income Ratio" },
        },
        tooltip: {
            shared: true,
            valueDecimals: 1,
            valueSuffix: "x",
        },
        plotOptions: {
            column: {
                pointPadding: 0.2,
                borderWidth: 0,
                grouping: true,
            },
        },
        series: [
            {
                name: "Black Households",
                data: blackRatios,
                color: "#bd1906",
            },
            {
                name: "White Households",
                data: whiteRatios,
                color: "#cc9e78",
            },
        ],
        legend: {
            itemStyle: { fontWeight: "bold" },
        },
    };
</script>

<Chart options={chartOptions} highcharts={Highcharts} />
