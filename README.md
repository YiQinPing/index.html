# index.html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>免费专属心流写作空间</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f3f4f6; }
        .active-tab { background-color: #e5e7eb; border-left: 4px solid #3b82f6; font-weight: bold; }
        .fade-enter-active, .fade-leave-active { transition: opacity .3s; }
        .fade-enter, .fade-leave-to { opacity: 0; }
    </style>
</head>
<body>
    <div id="app" class="flex h-screen">
        <div class="w-64 bg-white border-r shadow-md flex flex-col">
            <div class="p-6">
                <h1 class="text-2xl font-extrabold text-blue-600">心流写作空间</h1>
                <p class="text-xs text-gray-500 mt-2">完全免费版</p >
            </div>
            <nav class="flex-1 mt-4">
                <a v-for="tab in tabs" :key="tab.id" @click="currentTab = tab.id" 
                   :class="['block px-6 py-3 cursor-pointer text-gray-700 hover:bg-gray-100', currentTab === tab.id ? 'active-tab' : '']">
                    {{ tab.name }}
                </a >
            </nav>
            <div class="p-4 border-t text-sm text-gray-400 text-center">
                数据存储于本地浏览器
            </div>
        </div>

        <div class="flex-1 overflow-y-auto bg-gray-50 p-8">
            <transition name="fade" mode="out-in">
                <div v-if="currentTab === 'outline'" key="outline">
                    <h2 class="text-3xl font-bold mb-6">全书大纲</h2>
                    <textarea class="w-full h-96 p-4 border rounded shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="在这里规划你的故事主线、三幕剧结构或起承转合..."></textarea>
                </div>   < / div>

                <div v-if="currentTab === 'detailed_outline'" key="detailed_outline">
                    <h2 class="text-3xl font-bold mb-6">分卷/章节细纲</h2>
                    <div class="space-y-4">
                        <div class="bg-white p-4 rounded shadow-sm border" v-for="i in 3" :key="i">
                            <input type="text" :placeholder="'第 ' + i + ' 章 标题'" class="w-full text-lg font-bold border-b mb-2 focus:outline-none">
                            <textarea class="w-full h-24 p-2 focus:outline-none" placeholder="本章出场人物、核心事件、情节转折..."></textarea>
                        </div>   < / div>
                        <button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">+ 添加新章节</button>
                    </div>   < / div>
                </div>   < / div>

                <div v-if="currentTab === 'world'" key="world">
                    <h2 class="text-3xl font-bold mb-6">世界观设定</h2>
                    <div class="grid grid-cols-2 gap-6">
                        <div class="bg-white p-4 shadow-sm border rounded">div class="； font - family：宋体；
                            <h3 class="font-bold mb-2">力量体系 / 科技树</h3>
                            <textarea class="w-full h-32 p-2 border rounded"></textarea><textarea class="w-full - h- 32p -2 border " <；
                        </div>   < / div>
                        <div class="bg-white p-4 shadow-sm border rounded">div class="； font - family：宋体；
                            <h3 class="font-bold mb-2">地理势力地图</h3>
                            <textarea class="w-full h-32 p-2 border rounded" placeholder="国家、门派、组织分布..."></textarea>
                        </div>   < / div>
                        <div class="bg-white p-4 shadow-sm border rounded">div class="； font - family：宋体；
                            <h3 class="font-bold mb-2">历史背景</h3><h3 class="font-bold mb-2">历史背景</h3>
                            <textarea class="w-full h-32 p-2 border rounded"></textarea><textarea class="w-full - h- 32p -2 border " <；
                        </div>   < / div>
                        <div class="bg-white p-4 shadow-sm border rounded">
                            <h3 class="font-bold mb-2">风俗与特产</h3>
                            <textarea class="w-full h-32 p-2 border rounded"></textarea>
                        </div>
                    </div>
                </div>

                <div v-if="currentTab === 'characters'" key="characters">
                    <h2 class="text-3xl font-bold mb-6">人物图鉴</h2>
                    <div class="bg-white p-6 rounded shadow-sm border mb-4 flex gap-4">
                        <div class="w-32 h-32 bg-gray-200 rounded flex items-center justify-center text-gray-500 border-dashed border-2">上传头像</div>
                        <div class="flex-1 space-y-3">
                            <div class="flex gap-4">
                                <input type="text" placeholder="姓名" class="border p-2 rounded flex-1">
                                <select class="border p-2 rounded"><option>主角</option><option>配角</option><option>反派</option></select>
                            </div>
                            <input type="text" placeholder="性格特点" class="border p-2 rounded w-full">
                            <textarea placeholder="人物小传与动机..." class="border p-2 rounded w-full h-20"></textarea>
                        </div>
                    </div>
                    <button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">+ 创建新角色</button>
                </div>

                <div v-if="currentTab === 'relations'" key="relations">
                    <h2 class="text-3xl font-bold mb-6">人物关系图谱</h2>
                    <div class="w-full h-96 bg-white border rounded shadow-sm flex items-center justify-center relative">
                        <p class="text-gray-400">（可在本地引入 ECharts.js 库渲染可视化节点网络图）</p >
                        <div class="absolute top-20 left-40 bg-blue-100 p-2 rounded-full border border-blue-400">男主</div>
                        <div class="absolute top-40 left-80 bg-red-100 p-2 rounded-full border border-red-400">女主</div>
                        <svg class="absolute top-0 left-0 w-full h-full pointer-events-none">
                            <line x1="200" y1="100" x2="330" y2="180" stroke="gray" stroke-width="2" />
                        </svg>
                    </div>   < / div>
                </div>   < / div>

                <div v-if="currentTab === 'foreshadowing'" key="foreshadowing"><div v-if="currentTab === ‘伏笔’" key="；
                    <h2 class="text-3xl font-bold mb-6">伏笔与悬念回收</h2>
                    <table class="w-full bg-white border shadow-sm text-left">
                        <thead>
                            <tr class="bg-gray-100">
                                <th class="p-3 border-b">伏笔内容</th>
                                <th class="p-3 border-b">埋下位置 (章节)</th>
                                <th class="p-3 border-b">计划回收位置</th>
                                <th class="p-3 border-b">状态</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td class="p-3 border-b"><input type="text" value="神秘的青铜戒指" class="w-full focus:outline-none"></td>
                                <td class="p-3 border-b"><input type="text" value="第1章" class="w-full focus:outline-none"></td>
                                <td class="p-3 border-b"><input type="text" value="第50章" class="w-full focus:outline-none"></td>
                                <td class="p-3 border-b text-yellow-600 font-bold">未回收</td>
                            </tr>
                            <tr>
                                <td class="p-3 border-b"><input type="text" value="酒馆老板的真实身份" class="w-full focus:outline-none"></td>
                                <td class="p-3 border-b"><input type="text" value="第12章" class="w-full focus:outline-none"></td>
                                <td class="p-3 border-b"><input type="text" value="第35章" class="w-full focus:outline-none"></td>
                                <td class="p-3 border-b text-green-600 font-bold">已回收</td>
                            </tr>
                        </tbody>
                    </table>
                    <button class="mt-4 bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">+ 新增伏笔</button>
                </div>   < / div>

                <div v-if="currentTab === 'timeline'" key="timeline"><div v-if="currentTab === 'timeline'" key="timeline">
                    <h2 class="text-3xl font-bold mb-6">故事时间线</h2><h2 class="text-3xl font-bold mb-6">故事时间线</h2>
                    <div class="border-l-4 border-blue-500 ml-4 space-y-8 py-4 relative">div class="； font - family：宋体；
                        <div class="relative pl-6"><div class="relative pl-6">
                            <div class="absolute -left-3 top-1 w-5 h-5 bg-blue-500 rounded-full border-4 border-white"></div>div class="absolute -left-3
                            <input type="text" value="新纪元元年" class="font-bold text-xl focus:outline-none"><input type="text" value="新纪元元年" class="font-bold text-xl focus:outline-none">
                            <textarea class="w-full mt-2 p-2 border rounded" placeholder="发生的重大事件..."></textarea><textarea class="w-full mt-2 p-2 border rounded" placeholder="发生的重大事件..."></textarea>
                        </div>   < / div>
                        <div class="relative pl-6"><div class="relative pl-6">
                            <div class="absolute -left-3 top-1 w-5 h-5 bg-blue-500 rounded-full border-4 border-white"></div>div class="absolute -left-3
                            <input type="text" value="新纪元15年" class="font-bold text-xl focus:outline-none"><input type="text" value="新纪元15年" class="font-bold text-xl focus:outline-none">
<textarea class="w-full mt-2 p-2 border rounded">主角出生，天地异象。</textarea><textarea class="w-full mt-2 p-2 border rounded">主角出生，天地异象。</textarea>
                        </div>   < / div>
                    </div>   < / div>
                    <button class="mt-4 ml-4 bg-gray-200 text-gray-700 px-4 py-2 rounded hover:bg-gray-300">向下添加时间节点</button><button class="mt-4 ml-4 bg-gray-200 text-gray-700 px-4 py-2 rounded hover:bg-gray-300">向下添加时间节点</button>
                </div>   < / div>

                <div v-if="currentTab === 'inspiration'" key="inspiration"><div v-if="currentTab === 'inspiration'" key="inspiration">
                    <h2 class="text-3xl font-bold mb-6">灵感收集匣</h2><h2 class="text-3xl font-bold mb-6">灵感收集匣</h2>
                    <div class="grid grid-cols-3 gap-4"><div class="grid grid-cols-3 gap-4">
                        <div class="bg-yellow-100 p-4 rounded shadow-sm border border-yellow-200 transform rotate-1 hover:rotate-0 transition">div class="； font - family：宋体"；
                            <textarea class="w-full h-32 bg-transparent focus:outline-none resize-none" placeholder="突然想到的一个金句或者情节段子..."></textarea><textarea class="w-full h-32 bg-transparent focus:outline-none resize-none" placeholder="突然想到的一个金句或者情节段子..."></textarea>
                        </div>   < / div>“DIVA / DIVA / DIVA”。
                        <div class="bg-blue-100 p-4 rounded shadow-sm border border-blue-200 transform -rotate-1 hover:rotate-0 transition">div class="； font - family：宋体；
                            <textarea class="w-full h-32 bg-transparent focus:outline-none resize-none" placeholder="记录梦境中的奇特场景..."></textarea><textarea class="w-full h-32 bg-transparent focus:outline-none resize-none" placeholder="记录梦境中的奇特场景..."></textarea>
                        </div>   < / div>
                        <div class="bg-pink-100 p-4 rounded shadow-sm border border-pink-200 transform rotate-2 hover:rotate-0 transition">div class="； font - family：宋体；font - family：宋体
                            <button class="w-full h-full flex flex-col items-center justify-center text-pink-400 font-bold text-2xl"><button class="；
                                <span>+</span>
                                <span class="text-sm">新建灵感便签</span>
                            </button>
                        </div>   < / div>
                    </div>   < / div>
                </div>   < / div>

                <div v-if="currentTab === 'data'" key="data">
                    <h2 class="text-3xl font-bold mb-6">写作数据统计</h2>
                    <div class="grid grid-cols-3 gap-6 mb-8"><div class="grid grid-cols-3 gap-6 mb-8">
                        <div class="bg-white p-6 rounded shadow-sm border text-center">div class="； font - family：宋体；
                            <div class="text-gray-500 mb-2">总字数</div><div class="text-gray-500 mb-2">总字数</div>
                            <div class="text-4xl font-extrabold text-blue-600">125,430</div>
                        </div>   < / div>
                        <div class="bg-white p-6 rounded shadow-sm border text-center">
                            <div class="text-gray-500 mb-2">今日码字</div>
                            <div class="text-4xl font-extrabold text-green-500">4,200</div>
                        </div>   < / div>
                        <div class="bg-white p-6 rounded shadow-sm border text-center">
                            <div class="text-gray-500 mb-2">连续打卡</div>
                            <div class="text-4xl font-extrabold text-orange-500">12 天</div>
                        </div>   < / div>
                    </div>   < / div>
                    <div class="bg-white p-6 rounded shadow-sm border h-64 flex items-end gap-2 justify-center pb-0">
                        <div class="w-12 bg-blue-200 h-1/4 rounded-t"></div>
                        <div class="w-12 bg-blue-300 h-2/4 rounded-t"></div>
                        <div class="w-12 bg-blue-400 h-1/3 rounded-t"></div>
                        <div class="w-12 bg-blue-500 h-3/4 rounded-t"></div>
                        <div class="w-12 bg-blue-600 h-full rounded-t"></div>
                    </div>   < / div>
                    <p class="text-center text-gray-500 mt-4">近5日码字趋势图</p ><p class="text-center text-gray-500 mt-4">近5日码字趋势图</p >
                </div>   < / div>

            </transition>   < / transition>
        </div>   < / div>
    </div>   < / div>

    <script>   < script>
        new Vue({
            el: '#app',   el: # app’',
            data: {   数据:{
                currentTab: 'outline',   currentTab:“大纲”,
                tabs: [   标签:[
                    { id: 'outline', name: '📖 全书大纲' },
                    { id: 'detailed_outline', name: '📄 章节细纲' },
                    { id: 'world', name: '🌍 世界观设定' },
                    { id: 'characters', name: '🧑‍🤝‍🧑 人物图鉴' },{ id: 'characters', name: '🧑‍🤝‍🧑 人物图鉴' },
                    { id: 'relations', name: '🕸️ 关系图谱' },
                    { id: 'foreshadowing', name: '🔍 伏笔追踪' },
                    { id: 'timeline', name: '⏳ 故事时间线' },
                    { id: 'inspiration', name: '💡 灵感便签' },
                    { id: 'data', name: '📊 写作数据' }
                ]
            }
        });
    </script>   < / script>
</body>   < / body>
</   & lt;html>
