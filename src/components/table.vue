<template>
    <table>
        <thead>
            <th>#</th>
            <th>Nomi</th>
            <th>Modeli</th>
            <th>Kelgan vaqt</th>
            <th>Muddat</th>
        </thead>
        <tbody>
            <tr v-for="car, index of massiv">
                <td>{{ index + 1 }}</td>
                <td>{{ car.name }}</td>
                <td>{{ car.model }}</td>
                <td>{{ car.time.toLocaleString() }}</td>
                <td>{{ car.date }}</td>
            </tr>
        </tbody>
    </table>
</template>
<script>
export default {
    props: ['massiv']
}
</script>
<style lang="scss">
    table {
        width: 100%;
        margin-top: 40px;
        border-collapse: collapse;
        th,
        td {
            padding: 10px;
            border: 1px solid #333;
        }
    }
</style>