<template>
    <div>
        <Table ref="currentRowTable" :columns="columns3" :data="data1"></Table>
        <Button @click="handleClearCurrentRow">Clear</Button>
        <Button @click="handlerSelect"></Button>
        <div style="display: flex;width: 100%">
            <div :style="{width:ttWidth+'px'}">
                <Button @click="height += 200">改变宽度</Button>
            </div>
            <div style="flex: 1;overflow: hidden;">
                <Table :columns="columns3" :data="[]" :table-body-max-height="height" no-data-text="没有东西哦"></Table>
            </div>
        </div>

    </div>
</template>
<script>
    export default {
        data() {
            return {
                height: 500,
                columns3: [
                    {
                        type: 'selection',
                        width: 60,
                        align: 'center',
                    },
                    {
                        type: 'index',
                        width: 60,
                        align: 'center',
                        indexMethod(row) {
                            return row._index;
                        }
                    },
                    {
                        title: 'Name',
                        key: 'name',
                        align: 'center',
                    },
                    {
                        title: 'Age',
                        key: 'age',
                        align: 'center',
                        render(h, params) {
                            return h('div', {
                                style: {
                                    width: '500px',
                                    display: 'flex',
                                    'justify-content': 'space-between'
                                }
                            }, [
                                h('div', 'div1'),
                                h('div', 'div2')
                            ]);
                        }
                    },
                    {
                        title: 'Address',
                        key: 'address',
                        align: 'center',
                        tooltip: true
                    }
                ],
                data1: [
                    {
                        name: 'John Brown',
                        age: 18,
                        address: '自定义渲染列，使用 Vue 的 Render 函数。传入两个参数，第一个是 h，第二个为对象，包含 row、column 和 index，分别指当前行数据，当前列数据，当前行索引，详见示例。自定义渲染列，使用 Vue 的 Render 函数。传入两个参数，第一个是 h，第二个为对象，包含 row、column 和 index，分别指当前行数据，当前列数据，当前行索引，详见示例。自定义渲染列，使用 Vue 的 Render 函数。传入两个参数，第一个是 h，第二个为对象，包含 row、column 和 index，分别指当前行数据，当前列数据，当前行索引，详见示例。',
                        date: '2016-10-03',
                        _disabled: true
                    },
                    {
                        name: 'Jim Green',
                        age: 24,
                        address: 'London No. 1 Lake Park自定义渲染列，使用 Vue 的 Render 函',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joe Black',
                        age: 30,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Jon Snow',
                        age: 26,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    }
                ],
                ttWidth: 200
            }
        },
        methods: {
            handleClearCurrentRow() {
                this.$refs.currentRowTable.clearCurrentRow();
            },
            handlerSelect() {
                this.$refs.currentRowTable.toggleSelect(1);
            }
        }
    }
</script>

<style lang="less">
    .ivu-table table {
        width: 100% !important;
        font-size: 14px;
        color: #787878;
    }

</style>
