<template>
    <header :class="{ 'blur-background': blur }">
        <div class="header">
            <!-- 左侧logo -->
            <div class="logo">
                <a href="index.htm" title="桂电北海">
                    <img src="../assets/GUETlogo.png" alt="">
                </a>
            </div>
            <!-- 主菜单 -->
            <div class="header-menu" :class="{ 'header-menu-change-search': isChangeSearch }">
                <router-link active-class="active" to="/home">首页</router-link>
                <router-link active-class="active" to="/about">关于我们</router-link>
                <router-link active-class="active" to="/activities">活动回顾</router-link>

                <el-dropdown class="header-menu-dropdown">

                    <router-link active-class="active" to="/products">
                        <p>产品</p>
                        <el-icon>
                            <arrow-down />
                        </el-icon>
                    </router-link>

                    <template #dropdown>
                        <el-dropdown-menu>
                            <el-dropdown-item>
                                <router-link class="link" to="/translate">中文翻译</router-link>
                            </el-dropdown-item>
                            <el-dropdown-item>
                                <router-link class="link" to="/rewrite">文风转换</router-link>
                            </el-dropdown-item>
                            <el-dropdown-item>
                                <router-link class="link" to="/code2txt">代码翻译</router-link>
                            </el-dropdown-item>
                            <el-dropdown-item>
                                <router-link class="link" to="/xiaohongshuGenerator">小红书生成器</router-link>
                            </el-dropdown-item>
                            <el-dropdown-item divided>翻译</el-dropdown-item>
                        </el-dropdown-menu>
                    </template>
                </el-dropdown>
            </div>

            <!-- 搜索框 -->
            <div class="search-bar" :class="{ 'search-bar-change-search': isChangeSearch }">
                <label class="input-container">
                    <input type="text" @focusin="changeStyle" @focusout="changeStyle" placeholder="请输入关键字">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 56.966 56.966" fill="white" class="input-icon">
                        <path
                            d="M55.146 51.887L41.588 37.786A22.926 22.926 0 0046.984 23c0-12.682-10.318-23-23-23s-23 10.318-23 23 10.318 23 23 23c4.761 0 9.298-1.436 13.177-4.162l13.661 14.208c.571.593 1.339.92 2.162.92.779 0 1.518-.297 2.079-.837a3.004 3.004 0 00.083-4.242zM23.984 6c9.374 0 17 7.626 17 17s-7.626 17-17 17-17-7.626-17-17 7.626-17 17-17z" />
                    </svg>
                </label>
            </div>


            <!-- 头像区域 -->
            <div class="header-profile">
                <!-- 头像 -->
                <img class="profile-img" src="../assets/profile.png" alt="" @click="openDialog">
                <el-dialog v-model="centerDialogVisible" title="登录" width="30%" align-center>
                    <el-form ref="loginForm" :model="loginForm" :rules="rules" label-position="left" label-width="80px">
                        <el-form-item label="用户名" prop="username">
                            <el-input v-model="loginForm.username" autocomplete="off"></el-input>
                        </el-form-item>
                        <el-form-item label="密码" prop="password">
                            <el-input type="password" v-model="loginForm.password" autocomplete="off"></el-input>
                        </el-form-item>
                    </el-form>
                    <template #footer>
                        <span class="dialog-footer">
                            <el-button @click="centerDialogVisible = false">取消</el-button>
                            <el-button type="primary" @click="submitForm">登录</el-button>
                        </span>
                    </template>
                </el-dialog>

                <div class="notification">
                    <span class="notification-number">9</span>
                    <svg viewBox="0 0 1024 1024" xmlns="http://www.w3.org/2000/svg" data-v-029747aa="">
                        <path fill="currentColor"
                            d="M384 960v-64h192.064v64H384zm448-544a350.656 350.656 0 0 1-128.32 271.424C665.344 719.04 640 763.776 640 813.504V832H320v-14.336c0-48-19.392-95.36-57.216-124.992a351.552 351.552 0 0 1-128.448-344.256c25.344-136.448 133.888-248.128 269.76-276.48A352.384 352.384 0 0 1 832 416zm-544 32c0-132.288 75.904-224 192-224v-64c-154.432 0-256 122.752-256 288h64z">
                        </path>
                    </svg>
                </div>
                <svg viewBox="0 0 1024 1024" xmlns="http://www.w3.org/2000/svg" data-v-029747aa="">
                    <path fill="currentColor"
                        d="M764.416 254.72a351.68 351.68 0 0 1 86.336 149.184H960v192.064H850.752a351.68 351.68 0 0 1-86.336 149.312l54.72 94.72-166.272 96-54.592-94.72a352.64 352.64 0 0 1-172.48 0L371.136 936l-166.272-96 54.72-94.72a351.68 351.68 0 0 1-86.336-149.312H64v-192h109.248a351.68 351.68 0 0 1 86.336-149.312L204.8 160l166.208-96h.192l54.656 94.592a352.64 352.64 0 0 1 172.48 0L652.8 64h.128L819.2 160l-54.72 94.72zM704 499.968a192 192 0 1 0-384 0 192 192 0 0 0 384 0z">
                    </path>
                </svg>
            </div>
        </div>
        <div class="header-mobile">
            <!-- 左侧logo -->
            <div class="logo">
            </div>
            <div class="menu">
            </div>
        </div>
    </header>
</template>


<script>
//引入icon
import { ArrowDown } from '@element-plus/icons-vue'
import { mapGetters } from 'vuex';
import apiClient from "../views/apiClient";
import { ref } from 'vue'
export default {
    name: 'ElementplusIcon',
    components: {
        ArrowDown
    },

    data() {
        return {
            isChangeSearch: false,
            centerDialogVisible: false,
            loginForm: {
                username: '',
                password: ''
            },
            rules: {
                username: [
                    { required: true, message: '请输入用户名', trigger: 'blur' }
                ],
                password: [
                    { required: true, message: '请输入密码', trigger: 'blur' }
                ]
            }
        }
    },
    methods: {
        toggleBlur() {
            this.$store.commit('SET_BLUR', true);
        },
        openDialog() {
            this.centerDialogVisible = true;
        },
        submitForm() {
            this.$refs.loginForm.validate(async (valid) => {
                if (valid) {
                    try {
                        // const response = await this.$http.post('/login', this.loginForm);
                        const response = await apiClient.post('/auth/login', this.loginForm);
                        if (response.data.success) {
                            this.$message({
                                message: '登录成功',
                                type: 'success'
                            });
                            this.centerDialogVisible = false;
                        } else {
                            this.$message.error('用户名或密码错误');
                        }
                    } catch (error) {
                        this.$message.error('登录失败，请重试..');
                    }
                } else {
                    console.log('表单验证失败');
                    return false;
                }
            });
        }
    },
    computed: {
        ...mapGetters(['blur'])
    },

}

</script>

<style lang="scss" scoped>
.header {
    position: fixed;
    left: 0;
    top: 5px;
    z-index: 50;
    width: 100%;
    padding: 0 40px;
}

.header:before {
    content: '';
    position: absolute;
    top: -5px;
    left: 0;
    right: 0;
    height: 138px;
    background: url(../assets/bgq1.png) repeat-x;
    z-index: -1;
}

.header-menu-dropdown {
    cursor: pointer;
    display: flex;
    align-items: center;
}

.header-menu-dropdown a {
    font-size: 16px;
    text-decoration: none;
    height: 20px;
    align-content: baseline;
    align-items: baseline;
    justify-content: baseline;
    justify-items: baseline;
    text-align: bottom;
}

.header-menu-dropdown a>p {
    display: inline-block;
    margin-top: 3px;
}

.header-menu-dropdown a>.el-icon {
    position: absolute;
    margin-top: 3px;
}

.link {
    display: flex;
    align-items: center;
    white-space: nowrap;
    list-style: none;
    padding: 5px 16px;
    position: relative;
    padding: 5px 0;
    line-height: 20px;
    min-width: 10px;
    text-decoration: none;
    cursor: pointer;
    list-style: none;
    font-size: var(--el-font-size-base);
    color: var(--el-text-color-regular);
    --el-scrollbar-opacity: 0.3;
    --el-scrollbar-bg-color: var(--el-text-color-secondary);
    --el-scrollbar-hover-opacity: 0.5;
}

.el-dropdown-menu__item:hover .link {
    color: #409eff;
    /* 自定义的字体颜色 */
}

.header {
    // background-color: skyblue;
    display: inline-flex;
    align-items: center;
    flex-shrink: 0;
    height: 67px;
    width: 98%;
    border-bottom: 1px solid RGBA(113 119 144 / 25%);
    padding: 0 30px;
    white-space: nowrap;
    margin-top: 0px;

    @media screen and (max-width: 480px) {
        padding: 0 16px;
    }

    .logo {
        width: auto;
        height: 30px;
        margin-left: -80px;
        margin-right: 80px;
        flex-shrink: 0;
        display: flex;
        flex-direction: row;
        align-items: center;

        // @media screen and (max-width: 945px) {
        //     display: none;
        // }



    }

    .logo img {
        max-width: 70%;
        /* 根据需要调整百分比 */
        height: auto;
        /* 保持高度自动，以保持纵横比 */
    }

    /* .head-menu */
    &-menu,
    .header-menu-dropdown,
    .dropdown-item {
        display: flex;
        align-items: center;

        a {
            padding: 20px 30px;
            text-decoration: none;
            color: rgb(255, 255, 255);
            border-bottom: 2px solid transparent;
            transition: 0.3s;
            height: 23px;

            // @media screen and (max-width: 610px) {
            //     &:not(.main-header-link) {
            //         display: none;
            //     }
            // }

        }

        a:hover,
        a.active {
            color: #ffffff;
            border-bottom: 2px solid #ffffff;
        }

    }




    .search-bar {
        // opacity: 0.4;
        height: 40px;
        display: flex;
        width: 100%;
        max-width: 400px;
        padding-left: 16px;
        border-radius: 4px;
        border: none;

        .input-container {
            position: relative;
        }

        input {
            width: 100%;
            height: 100%;
            border: none;
            outline: none;
            border: 1px solid rgb(207, 207, 207);
            background-color: #ffffff;
            background-color: rgba(255, 255, 255, 0);
            border-radius: 20px;
            font-family: "Poppins", sans-serif;
            font-size: 15px;
            font-weight: 500;
            padding: 0 20px 0 40px;

            &::placeholder {
                font-family: "Poppins", sans-serif;
                color: rgb(156, 156, 156);
                font-size: 15px;
                font-weight: 500;
            }
        }

        .input-icon {
            width: 14px;
            height: 14px;
            position: absolute;
            left: 16px;
            top: 50%;
            transform: translateY(-50%);
        }

        // 点击输入后边框改变颜色or只是变粗
        input:focus {
            border: 2px solid rgba(255, 255, 255, 0.675);
            // border: 2px solid rgb(98, 163, 203);
        }

    }

    .header-profile {
        display: flex;
        align-items: center;
        //text-align: center;
        padding: 0 16px 0 40px;
        margin-left: auto;
        flex-shrink: 0;

        svg {
            width: 22px;
            color: #f9fafb;
            flex-shrink: 0;
        }

        .notification {
            position: relative;
            top: 2px;

            &-number {
                position: absolute;
                background-color: #3a6df0;
                width: 16px;
                height: 16px;
                border-radius: 50%;
                font-size: 10px;
                display: flex;
                align-items: center;
                justify-content: center;
                color: #fff;
                right: -6px;
                top: -6px;
            }

            &+svg {
                margin-left: 22px;

                @media screen and (max-width: 945px) {
                    display: none;
                }
            }
        }

        // 头像
        .profile-img {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid #f9fafb;
            margin-left: 22px;
            margin-right: 22px;
            cursor: pointer;
        }
    }

    /*输入框聚焦后，样式改变 */

    .header-menu-change-search {
        display: none;
    }

    .search-bar-change-search {
        max-width: 600px;
        margin: auto;
        transition: 0.4s;
        box-shadow: 0 0 0 1px RGBA(113 119 144 / 25%);
        padding-left: 0;
    }

}

.blur-background {
    filter: blur(4px);
}

.custom-dialog {
    position: absolute;
    z-index: 9999;
}

.higher-z-index {
    z-index: 9999;
}

.dialog-footer button:first-child {
    margin-right: 10px;
}

.header-mobile {
    display: none;
}

@media screen and (max-width: 1400px) {
    .header {
        display: none;
        width: 0;
    }

    .header-mobile {
        position: fixed;
        left: 0;
        top: 0.71vh;
        z-index: 50;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-shrink: 0;
        height: 7.37vh;
        border-bottom: 0.14vh solid RGBA(113 119 144 / 25%);
    }

    .header-mobile:before {
        content: '';
        position: absolute;
        top: -0.61vh;
        left: 0;
        right: 0;
        height: 8.07vh;
        background: url(../assets/bgq1.png) repeat-x;
        z-index: -1;
    }

    .logo {
        flex-grow: 1;
        max-width: 60vw; // 修改宽度百分比以调整 logo 大小
        height: 4.86vh;
        max-height: 4.86vh; // 限制 logo 的最大高度
        margin-left: 1%;
        flex-shrink: 0;
        display: flex;
        align-items: center;
        background: url("../assets/GUETlogo.png") no-repeat center;
        background-size:contain; // 修改为 contain 以保持 logo 完整且在其容器内
    }

    .menu {
        flex-grow: 0;
        width: 5%;
        height: 4.29vh;
        margin-right: 1%;
        background: url(../assets/iconq2.png) center center no-repeat;
        background-size: cover;
    }
}



</style>