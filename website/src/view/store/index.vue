<template>
    <div>
        <div style="margin-bottom: 10px;">
            <a-button type="primary" @click="create">创建门店</a-button>
        </div>
        <div>
            <a-table :columns="columns" :data-source="list">
                <div slot="action" slot-scope="text">
                    <a-button type="block" @click="edit">编辑</a-button>
                    <a-button type="danger" @click="remove">删除</a-button>
                </div>
            </a-table>
        </div>
        <a-modal v-model="visible" title="门店信息" @ok="handleOk" width="900px">
            <a-form-model ref="ruleForm" :model="form" :label-col="labelCol" :wrapper-col="wrapperCol">
                <a-form-model-item label="门店名称" required prop="name">
                    <a-input v-model="form.name" />
                </a-form-model-item>
                <a-form-model-item label="门店电话" required prop="tel">
                    <a-input v-model="form.tel" type="number" />
                </a-form-model-item>
                <a-form-model-item label="营业时间" required prop="beginTime">
                    <a-time-picker format="HH:mm" v-model="form.beginTime" />~
                    <a-time-picker format="HH:mm" v-model="form.endTime" />
                </a-form-model-item>
                <a-form-model-item label="地址" required prop="addrDetail">
                    <a-cascader :options="addrOptions" v-model="form.addr" placeholder="Please select" @change="addrChange" />
                    <div>
                        <label>详细地址：</label>
                        <a-textarea v-model="form.addrDetail" placeholder="" :auto-size="{ minRows: 3, maxRows: 5 }" />
                    </div>
                </a-form-model-item>
            </a-form-model>

        </a-modal>
    </div>
</template>

<script>
export default {
    name: 'Store',
    data() {
        return {
            visible: false,
            labelCol: { span: 4 },
            wrapperCol: { span: 14 },
            form: { addr: [] },
            addrOptions: [{ value: "广东", 'label': '广东', children: [{ value: '深圳', label: '深圳', children:[{value: '罗湖', label: '罗湖'}] }] }, { value: '北京', label: '北京' }],
            columns: [
                {
                    title: '门店名称',
                    dataIndex: 'name',
                    key: 'name',
                },
                {
                    title: '门店地址',
                    dataIndex: 'address',
                    key: 'address',
                    ellipsis: true,
                },
                {
                    title: '电话号码',
                    dataIndex: 'tel',
                    key: 'tel',
                    ellipsis: true,
                },
                {
                    title: '营业时间',
                    dataIndex: 'businessHours',
                    key: 'businessHours',
                    ellipsis: true,
                },
                {
                    title: '操作',
                    key: 'operation',
                    fixed: 'right',
                    width: 200,
                    scopedSlots: { customRender: 'action' },
                }
            ],
            list: [
                {
                    key: '1',
                    name: '初见喜美',
                    tel: 18658695488,
                    address: 'New York No. 1 Lake Park, New York No. 1 Lake Park',
                    businessHours: '10~22',
                },
                {
                    key: '2',
                    name: '初见喜美2',
                    tel: 13169685478,
                    address: 'London No. 2 Lake Park, London No. 2 Lake Park',
                    businessHours: '10~22',
                },
                {
                    key: '3',
                    name: '初见喜美3',
                    tel: 1256489,
                    address: 'Sidney No. 1 Lake Park, Sidney No. 1 Lake Park',
                    businessHours: '10~22',
                },
            ],
        }
    },
    methods: {
        handleOk() {
            this.$refs.ruleForm.validate(valid => {
                if (valid) {
                    this.form.addr = this.form.addr.join('/');
                    alert('submit!');
                    this.visible = false;
                } else {
                    this.$message.error('输入错误');
                    return false;
                }
            })
        },
        create() {
            this.visible = true;
        },
        edit() {

        },
        remove() {
            alert('remove!');
        },
        addrChange(value) {
            console.log('/'.join(value));
        }
    }
}
</script>
  
<style></style>