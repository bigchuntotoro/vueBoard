<template>
    <div>
        <el-table border :data="boardList" @row-click="clickRow">
            <el-table-column prop="bno" label="글번호"></el-table-column>
            <el-table-column prop="title" label="제목"></el-table-column>
            <el-table-column prop="content" label="내용"></el-table-column>
            <el-table-column :min-width="20" prop="writer" label="작성자"> </el-table-column>
            <el-table-column :min-width="33" prop="regDate" label="등록일" :formatter="DateFormat"></el-table-column>
        </el-table>
        <board-detail ref="detailPopup" @reload="getBoardList()"></board-detail>
    </div>
</template>

<script>
    import axios from 'axios';
    import moment from 'moment';
    import BoardDetail from './BoardDetail';

    export default {
        name: 'BoardList',
        components: { BoardDetail },
        data() {
            return {
                boardList: [],
            };
        },
        created() {
            this.getBoardList();
        },
        methods: {
            DateFormat(row) {
                return moment(row.regDate).format('YYYY-MM-DD hh:MM:ss');
            },
            getBoardList() {
                axios
                    .get('http://localhost:8081/board/get-board-list.do')
                    .then((response) => {
                        if (response.data.success) {
                            this.boardList = response.data.result;
                        }
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
            },
            clickRow(row) {
                this.$refs.detailPopup.getBoardDetail(row);
            },
        },
    };
</script>

<style scoped></style>