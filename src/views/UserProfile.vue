<template>
    <ContentBase>
        <div class="row">
            <div class="col-3">
                <UserProfileInfo @follow="follow" @unfollow="unfollow" :user="user" />
                <UserProfileWrite @post_a_post="post_a_post" />
            </div>
            <div class="col-9">
                <UserProfilePosts :posts="posts" />
            </div>
        </div>
    </ContentBase>
</template>

<script>
    import ContentBase from "@/components/ContentBase.vue";
    import UserProfileInfo from "@/components/UserProfileInfo.vue";
    import UserProfilePosts from "@/components/UserProfilePosts.vue";
    import UserProfileWrite from "@/components/UserProfileWrite.vue";
    import { reactive } from "vue";
    export default {
        name: "UserProfile",
        components: {
            ContentBase,
            UserProfileInfo,
            UserProfilePosts,
            UserProfileWrite,
        },
        setup() {
            const user = reactive({
                id: 1,
                username: "tangzuhan",
                lastName: "Tang",
                firstName: "Zuhan",
                followerCount: 0,
                is_followed: false,
            });

            const follow = () => {
                if (user.is_followed) return;
                user.is_followed = true;
                user.followerCount++;
            }
            
            const unfollow = () => {
                if (!user.is_followed) return;
                user.is_followed = false;
                user.followerCount--;
            }

            const post_a_post = (content) => {
                if (content === "") return;
                posts.count++;
                posts.posts.unshift({
                    id: posts.count,
                    useId: 1,
                    content: content,
                });
            }

            const posts = reactive({
                count: 3,
                posts: [
                    {
                        id: 1,
                        userId: 1,
                        content: "啦啦啦啦啦啦啦啦啦啦",
                    },
                    {
                        id: 2,
                        userId: 1,
                        content: "啦啦啦啦啦德玛西亚",
                    },
                    {
                        id: 3,
                        userId: 1,
                        content: "啦啦啦啦啦啦啦艾欧尼亚",
                    }
                ]
            });

            return {
                user,
                follow,
                unfollow,
                posts,
                post_a_post,
            }
        }
    }
</script>

<style scoped>

</style>