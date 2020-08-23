<table id="table" class="w-full">
  <thead>
    <tr>
      <th
        v-for="(head, i) in headers"
        :key="i"
        @click="addStringToQuery(head.toLowerCase())"
        class="cursor-pointer bg-gray-300 border-b-2 text-xs font-semibold px-1"
      >
        {{head}}
      </th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(row, ri) in data" :key="ri" class="group">
      <td
        v-for="(head, i) in headers"
        :key="i"
        @click="addStringToQuery(row[head])"
        class="cursor-pointer group-hover:bg-blue-100 border-t border-l px-1 text-center"
        :class="{'bg-gray-100': ri % 2 !== 0}"
      >
        {{row[head]}}
      </td>
    </tr>
  </tbody>
</table>
