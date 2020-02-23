<template>
    <div style="margin: 30px;">
        <client-only>
            <vue-editor
                v-model="inputText"
                id="editor"
                useCustomImageHandler
                @image-added="handleImageAdded"
            ></vue-editor>
        </client-only>
    </div>
</template>

<script>
export default {
    data() {
        return {
            // 编辑器双向数据绑定的变量
            inputText: ""
        };
    },
    methods: {
        handleImageAdded: function(
            file,
            Editor,
            cursorLocation,
            resetUploader
        ) {
            // An example of using FormData
            // NOTE: Your key could be different such as:
            // formData.append('file', file)

            var formData = new FormData();
            formData.append("files", file);

            this.$axios({
                url: "/upload",
                method: "POST",
                data: formData
            })
            .then(result => {
                let url = this.$axios.defaults.baseURL + result.data[0].url; // Get url from response
                Editor.insertEmbed(cursorLocation, "image", url);
                resetUploader();
            })
            .catch(err => {
                console.log(err);
            });
        }
    }
};
</script>

<style>
</style>