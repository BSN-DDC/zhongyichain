## 平台接入 官方DDC 准备工作

1.   DID申请：

     平台方 使用  bsn  提供的 DID Sdk 生成 DID. 保存好密钥；举例 申请的did为: did:bsn:3wxYHXwAm57grc9JUr2zrPHt9HC

2.   opb EOS账户创建：

     平台方需要在[bsn门户](https://bsnbase.com/)  创建 EOS 账户， 参考帮助说明 **[OPB 链账户管理](https://bsnbase.com/static/tmpFile/bzsc/openper/7-2-1.html)** ;   举例 平台方的账户为：plateacco111

    3.  平台方需要为 EOS账户 购买账户资源(RAM、NET、CPU)；
    3.  平台方需要向bsn-ddc 运营商 提供（eos账户名、平台方DID信息）申请成功平台方角色
    3.  平台方需要向bsn-ddc 运营商购买业务费 ；
    3.  平台方可以使用 bsn-ddc官方提供的 sdk， 进行 ddc 的 发行、流转等操作。 

​	

## 连接信息

1. Eos opb网关地址信息：  https://opbtest.bsngate.com:18602/api/733067cef23441daaf8dfe5fadd82cc8/rpc
2. Eos 官方DDC 合约部署账户为： chinabsnddc1

### 以下为 已经创建好的 平台账户以及其所属的终端用户

```json
// 平台账户: plateacco111  业务费 500.0
"plateacco111":{
    "privateKey":"5KdrEgqsaTXwwnriZQQoXhDhZUFQhy3a51jaTxQ85qY5WntCwGH",
    "publicKey":"EOS62s8ox63Uuvb1iEDMsBPyHL1Mdrscj4j38gATctAyFheDqKaFE"
  },
//平台账户plateacco111 下终端用户  业务费各包含 100.0
 "commonacc111":{
    "privateKey":"5JZ5R38KqoM7TQo1oB8VDQi6ZiepnZs4FmKjs6uLH1omiuVGay1",
    "publicKey":"EOS5z6U19Rwp8X8vcmZrNi4iocHbmrcpS8S84ibsW4kqxsNUTmNFe"
  },
  "commonacc112":{
    "privateKey":"5KbWmi8HRpvFqd3ZDaA66xCAXpEugfgknZqn13bSmH1gj5ipJgy",
    "publicKey":"EOS5BRENdjQwwY7yS8fcHz4zuC83BdqcVvvJd9jc5wxk1zLNG1Yci"
  },
  "commonacc113":{
    "privateKey":"5K5cvpFLwsfe3oh1J2y8ipb1Bji2VXvEjhK6Taax8Y1S7do1x7u",
    "publicKey":"EOS8R454EXEUE8drVY4zWLVWUpawVMGz4HhGASmhmP9VPnEUfZ5Xj"
  },

----------------------------------------分割线---------------------------------------------------

// 平台账户: plateacco112  业务费 500.0
  "plateacco112":{
    "privateKey":"5JpRaxKm3D1wFgLvux8RZ3d8asnsh3uyDVCaoKkG15Hnm6M3Hew",
    "publicKey":"EOS6VYgur1mktPycGmmsZySxobE4r3yYLf5a9nCYnDgncY2Kkku46"
  },
 //平台账户plateacco112 下终端用户  业务费各包含 100.0
  "commonacc121":{
    "privateKey":"5JZ5R38KqoM7TQo1oB8VDQi6ZiepnZs4FmKjs6uLH1omiuVGay1",
    "publicKey":"EOS5z6U19Rwp8X8vcmZrNi4iocHbmrcpS8S84ibsW4kqxsNUTmNFe"
  },
  "commonacc122":{
    "privateKey":"5KbWmi8HRpvFqd3ZDaA66xCAXpEugfgknZqn13bSmH1gj5ipJgy",
    "publicKey":"EOS5BRENdjQwwY7yS8fcHz4zuC83BdqcVvvJd9jc5wxk1zLNG1Yci"
  },
  "commonacc123":{
    "privateKey":"5K5cvpFLwsfe3oh1J2y8ipb1Bji2VXvEjhK6Taax8Y1S7do1x7u",
    "publicKey":"EOS8R454EXEUE8drVY4zWLVWUpawVMGz4HhGASmhmP9VPnEUfZ5Xj"
  },
  
```

