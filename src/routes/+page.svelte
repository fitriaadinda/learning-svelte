<script>
    
    import DropDown from "../lib/dropDown.svelte";
    import ListOption from "../lib/listOption.svelte";

    // let options = [
    //     {
    //         groupName: "Alaska/ Hawaiian Timezone",
    //         options: [
    //             { value: "AKST", label: "Alaska Standard Time" },
    //             { value: "HST", label: "Hawaiian Standard Time" }
    //         ]
    //     },
    //     {
    //         groupName: "Pacific Timezone",
    //         options: [
    //             { value: "PST", label: "Pacific Standard Time" },
    //             { value: "PDT", label: "Pacific Daylight Time" }
    //         ]
    //     }
    // ]

    let dropdownoption = [
        {
            groupName: "Alaskan/ Hawaiian Timezone",
            options: [
                { value: "AKST", label: "Alaska Standard Time" },
                { value: "HST", label: "Hawaiian Standard Time" }
            ]
        },
        {
            groupName: "Pacific Timezone",
            options: [
                { value: "PST", label: "Pacific Standard Time" },
                { value: "PDT", label: "Pacific Daylight Time" }
            ]
        }
    ]

    let selectedOption = null;

    function handleSelect(option) {
        selectedOption = option;
    }
</script>

<!-- <ListOption options={options} /> -->
<DropDown options={dropdownoption} selectedOption={selectedOption}/>

<style>
</style>  