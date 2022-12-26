<template>
    <div>
        <h1>Fevereiro</h1>
        <table class="">
            <tr class="row">
                <th class="tst">Data</th>
                <th>Descrição</th>
                <th>Tipo</th>
                <th>Quantidade</th>
            </tr>
            <tr>
                <td>
                    <input type="date" id="data">
                </td>
                <td>
                    <input type="text" class="desc">
                </td>
                <td>
                    <select name="" id="">
                        <option value="0">Gasto</option>
                        <option value="1">Ganho</option>
                    </select>
                </td>
                <td class="din">
                    R$
                    <input type="number">
                </td>
            </tr>
        </table>
    </div>
</template>

<script>

export default {
    name: 'fevereiro',
}

</script>

<style>

table {
    width: 500px;
    border: 1px solid;
}

th{
    border: 1px solid black;
    text-align: center;
}
.din {
    display:flex;
}

</style>