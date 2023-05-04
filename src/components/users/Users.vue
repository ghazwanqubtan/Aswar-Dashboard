<template>
    <h4>
        Users List
    </h4>
    <br/>
    <CTable align="middle" class="mb-0 border" hover responsive>
              <CTableHead color="light">
                <CTableRow>
                  <CTableHeaderCell class="text-center">
                    <CIcon name="cil-people" />
                  </CTableHeaderCell>
                  <CTableHeaderCell>User</CTableHeaderCell>
                  <CTableHeaderCell>Email</CTableHeaderCell>
                  <CTableHeaderCell>Created Date</CTableHeaderCell>
                  
                  
                </CTableRow>
              </CTableHead>
              <CTableBody>
                <CTableRow v-for="item in tableExample" :key="item.name">
                  <CTableDataCell class="text-center">
                    <CAvatar
                      size="md"
                      :src="item.avatar.src"
                      :status="item.avatar.status"
                    />
                  </CTableDataCell>
                  <CTableDataCell>
                    <div>{{ item.user.name }}</div>
                  </CTableDataCell>
                  <CTableDataCell>
                    <div>{{ item.user.email }}</div>
                  </CTableDataCell>
                  <CTableDataCell>
                    <div>{{ item.user.createdAt }}</div>
                  </CTableDataCell>
                </CTableRow>
                <CTableRow> </CTableRow>
              </CTableBody>
            </CTable>

</template>



<script>

import avatar1 from '@/assets/images/avatars/1.jpg'
import avatar2 from '@/assets/images/avatars/2.jpg'
import avatar3 from '@/assets/images/avatars/3.jpg'

import { CTableHeaderCell } from '@coreui/vue'



export default {
    name: "Users",
    setup() {
        const tableExample = [
            {
                avatar: { src: avatar1, status: "success" },
                user: {
                    name: "Yiorgos Avraamu",
                    email: "yiorgos@gmail.com",
                    createdAt: "Jan 1, 2021",
                },
            },
            {
                avatar: { src: avatar2, status: "warning" },
                user: {
                    name: "Ali Rahem",
                    email: "ali6Rahem@gmail.com",
                    createdAt: "Jan 1, 2022",
                },
            },
            {
                avatar: { src: avatar3, status: "danger" },
                user: {
                    name: "Hussien yas",
                    email: "huss6yas@gmail.com",
                    createdAt: "Jan 5, 2022",
                },
            },
            
        ];
        return {
            tableExample,
        };
    },
    components: { CTableHeaderCell }
}
</script>