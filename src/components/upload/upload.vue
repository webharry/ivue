<template>
    <div id="uploader" class="wu-example">
        <!--用来存放文件信息-->
        <div id="thelist" class="uploader-list"></div>
        <div class="btns">
            <div id="picker">选择文件</div>
            <button id="ctlBtn" class="btn btn-default">开始上传</button>
        </div>
        <Upload action="//jsonplaceholder.typicode.com/posts/" @on-success="handleSuccess">
            <Button icon="ios-cloud-upload-outline">Upload files</Button>
        </Upload>
        <!-- <button id="ctlBtn" class="btns">上传</button> -->
        <!-- <vue-upload-web upload-button=".btns" :url="cdnUrl" :accept="accept" :key-generator="keyGenerator" @progress="uploadProgress" @success="handleSuccess" @error="error" @complete="handleComplete"></vue-upload-web> -->
    </div>
</template>
<script>
    import jQuery from 'jquery'
    import './js/webuploader.js'

	var $ = jQuery,
        $list = $('#thelist'),
        $btn = $('#ctlBtn'),
        state = 'pending',
        uploader;
    
	var uploader = WebUploader.create({

	    // swf文件路径
	    swf: '/libs/webuploader/0.1.5/Uploader.swf',

	    // 文件接收服务端。
	    server: 'http://webuploader.duapp.com/server/fileupload.php',

	    // 选择文件的按钮。可选。
	    // 内部根据当前运行是创建，可能是input元素，也可能是flash.
	    pick: '#picker',

	    // 不压缩image, 默认如果是jpeg，文件上传前会压缩一把再上传！
	    resize: false
	});

	// 当有文件被添加进队列的时候
	uploader.on( 'fileQueued', function( file ) {
	    $list.append( '<div id="' + file.id + '" class="item">' +
	        '<h4 class="info">' + file.name + '</h4>' +
	        '<p class="state">等待上传...</p>' +
	    '</div>' );
	});

	// 文件上传过程中创建进度条实时显示。
	uploader.on( 'uploadProgress', function( file, percentage ) {
	    var $li = $( '#'+file.id ),
	        $percent = $li.find('.progress .progress-bar');

	    // 避免重复创建
	    if ( !$percent.length ) {
	        $percent = $('<div class="progress progress-striped active">' +
	          '<div class="progress-bar" role="progressbar" style="width: 0%">' +
	          '</div>' +
	        '</div>').appendTo( $li ).find('.progress-bar');
	    }

	    $li.find('p.state').text('上传中');

	    $percent.css( 'width', percentage * 100 + '%' );
	});

	uploader.on( 'uploadSuccess', function( file ) {
	    $( '#'+file.id ).find('p.state').text('已上传');
	});

	uploader.on( 'uploadError', function( file ) {
	    $( '#'+file.id ).find('p.state').text('上传出错');
	});

	uploader.on( 'uploadComplete', function( file ) {
	    $( '#'+file.id ).find('.progress').fadeOut();
	});

    uploader.on( 'all', function( type ) {
        if ( type === 'startUpload' ) {
            state = 'uploading';
        } else if ( type === 'stopUpload' ) {
            state = 'paused';
        } else if ( type === 'uploadFinished' ) {
            state = 'done';
        }

        if ( state === 'uploading' ) {
            $btn.text('上传中');
        } else {
            $btn.text('上传')
        }
    });

    $btn.on( 'click', function() {
        if ( state === 'uploading' ) {
            uploader.stop();
        } else {
            uploader.upload();
        }
    });

export default {
    name: 'xUpload',
    data() {
        return {
            cdnUrl:'http://webuploader.duapp.com/server/fileupload.php',
            accept:null
        }
    },
    computed:{
        
    },
    methods:{
        uploadProgress(){
            console.log('正在上传...')
        },
        handleSuccess(){
            console.log('上传成功')
        },
        error(){
            console.log('上传失败')
        },
        handleComplete(){
            console.log('上传完成')
        },
        keyGenerator: function(file) {
            const currentTime = new Date().getTime();
            const key = currentTime + "." + file.name;
            return key;
        }
    },
    created(){
    }
}
</script>
<style scoped>
.webuploader-container {
	position: relative;
}
.webuploader-element-invisible {
	position: absolute !important;
	clip: rect(1px 1px 1px 1px); /* IE6, IE7 */
    clip: rect(1px,1px,1px,1px);
}
.webuploader-pick {
	position: relative;
	display: inline-block;
	cursor: pointer;
	background: #00b7ee;
	padding: 10px 15px;
	color: #fff;
	text-align: center;
	border-radius: 3px;
	overflow: hidden;
}
.webuploader-pick-hover {
	background: #00a2d4;
}

.webuploader-pick-disable {
	opacity: 0.6;
	pointer-events:none;
}
</style>

