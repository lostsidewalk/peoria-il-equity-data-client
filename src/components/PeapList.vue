<template>
    <div>
        <v-data-table 
            :headers="headers"
            :items="dataTableItems"
            item-value="name"
            :expanded="expanded"
            :show-expand="true"
            :expand-on-click="true"
            items-per-page="-1"
            density="compact"
            :fixed-header="true"
            height="65svh"
            hover
            multi-sort
            sticky
            >
            <template #top>
                PEAP List
            </template>
            <template #expanded-row="{ columns, item }">
                <tr>
                    <td :colspan="columns.length">
                        {{ item.business_description }}
                    </td>
                </tr>
            </template>
        </v-data-table>
    </div>
</template>

<script setup>
import { reactive, onMounted } from 'vue';

onMounted(async () => {
    const response = await fetch('https://peoria-il-equity-data-api.onrender.com/peap');
    const data = await response.json();
    for (let i = 0; i < data.length; i++) {
        let item = data[i];
        dataTableItems.push(item);
    }
});

const headers = [
    { title: "Name", key: "name", sortable: true },
    // { title: "Business Description", key: "business_description" },
    // { title: "Certification Information", key: "certification_information" },
    { title: "Contact", key: "contact", sortable: true },
    { title: "Email", key: "email", sortable: true },
    // { title: "Location", key: "location" },
    { title: "Ownership", key: "ownership_text", sortable: true },
    { title: "African-American", key: "owner_african_american", sortable: true },
    // { title: "Asian", key: "owner_asian", sortable: true },
    // { title: "Female", key: "owner_female", sortable: true },
    // { title: "Hispanic", key: "owner_hispanic", sortable: true },
    // { title: "Veteran", key: "owner_veteran", sortable: true },
    { title: "Phone", key: "phone", sortable: true },
    { title: "Website", key: "website", sortable: true },
];

const dataTableItems = reactive([]);

const expanded = reactive([]);

</script>
