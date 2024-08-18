module.exports.config = {
    name: "join",
    version: "1.0.0",
    hasPermssion: 0,
    credits: "ManhG",
    description: "Bật tắt joinNoti",
    commandCategory: "Qtv",
    usages: "",
    cooldowns: 2
};

module.exports.languages = {
  "vi": {"on": "✅ Bật","off": "✅ Tắt","successText": "gửi tin nhắn chào mừng khi có thành viên mới tham gia nhóm chat",},
  "en": {"on": "on","off": "off","successText": "send a welcome message when a new member joins your chat group",}
}
const fs = require('fs')
const path = __dirname + '/data/dataEvent.json'
exports.onLoad = o=>{
  if (!fs.existsSync(path))fs.writeFileSync(path, '{}')
}
module.exports.run = async function ({ api, event, Threads, getText }) {
  let data = JSON.parse(fs.readFileSync(path))
  const { threadID, messageID } = event;
  if (!data.join)data.join = []
  let find = data.join.find(i => i.threadID ==threadID);

  if(find) find.status = !find.status?true:false;else find = data.join.push({
         threadID,
         status: true
       });
   fs.writeFileSync(path, JSON.stringify(data,null,4),'utf8')
  return api.sendMessage(`${!find.status ? getText("off") : getText("on")} ${getText("successText")}`, threadID, messageID);
}