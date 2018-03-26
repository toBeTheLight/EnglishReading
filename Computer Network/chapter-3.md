# chapter-3

* Residing between the application and network layers, the transport layer is a central piece of the layered network architecture.
  - reside 位于 [rɪ'zaɪd]
  - central piece 中央部分
  - architecture 架构 ['ɑrkə'tɛktʃɚ]

* It has the critical role of providing communication services directly to the application processes running on different hosts.
  - critical 关键 ['krɪtɪkl]
  - communication 通讯 [kə,mjunɪ'keʃən]
  - process 进程、过程 [proˈsɛs;(for n.)prɑsɛs]

* The pedagagic approach we take in this chapter is to alternate between discussions of transport-layer principles and discussions of how these principles are implemented in existing protocols.
  - pedagagic 教学的 [,pɛdə'ɡɑdʒɪk]
  - approach 方法 [ə'protʃ]
  - alternate 交流、轮流 [ˈɔltɚˌnet;(for adj.)ˈɔ:ltərnət]
  - principles 原理 ['prɪnsəpl]
  - implement 实现、生效 ['ɪmplɪmɛnt]
  - exist 存在 [ɪɡ'zɪst]

* As usual, particular emphasis will be given to Internet protocols, in particular the TCP and UDP transport-layer protocols.
  - particular 特别的、详细的 [pɚ'tɪkjəlɚ]
  - emphasis 重点 ['ɛmfəsɪs]

* This sets the stage for examining the first critical function of the transport layer -- extending the network layer's delivery service between two end systems to a delivery service between two application-layer processes running on the end system.
  - stage 阶段，台子 [stedʒ]
  - examine 检查 [ɪg'zæmɪn]
  - extend 扩展 [ɪk'stɛnd]
  - delivery 交付、传递 [dɪ'lɪvəri]
  - end systems （终）端系统

* We'll illustrate this function in our coverage of the Internet's connectionless transport protocol, UDP.
  - illustrate 阐明 [ˈɪləˌstret, ɪˈlʌsˌtret]
  - coverage 覆盖（范围 ）[ˈkʌvərɪdʒ]

* We'll then return to principles and confront one of the most fundamental problems in computer networking--how two entities can communicate reliably over a medium that may lose and corrupt data.
  - confront 比较、面对 [kən'frʌnt]
  - fundamental 基本的、根本的   [,fʌndə'mɛntl]
  - entity 存在、实体 ['ɛntəti]
  - reliably 可靠地 [rɪˈlaɪəblɪ]
  - medium 媒介、中间 [ˈmidiəm]
  - corrupt 腐化、损毁 [kəˈrʌpt]

* Through a series of increasingly complicated (and realistic) scenarios, we'll build up an array of techniques that transport protocols use to solve this problem.
  - complicate 复杂的 [ˈkɑ:mplɪkeɪt]
  - realistic 现实的、逼真的 [ˌriəˈlɪstɪk]
  - scenario 情景、方案 [səˈnærioʊ]
  - technique 技术 [tɛkˈnik]

* We'll then show how these principles are embodied in TCP, the Internet's connection-oriented transport protocol.
  - embody 表现、象征 [ɪmˈbɑ:di]
  - orient 以...为方向 [ˈɔriənt]
  - connection-oriented 面向连接的

* We'll next move on to a second fundamentally important problem in networking--controlling the transmission rate of transport-layer entities in order to avoid, or recover from, congestion within the network.
  - transmission 传送 [trænsˈmɪʃən]
  - rate 速度、比率 [ret]
  - recover from 恢复
  - congestion 拥挤 [kənˈdʒestʃən]

* We'll consider the causes and consequences of congestion, as well as commonly used congestion-control techniques.
  - consequence 后果 [ˈkɑ:nsəkwens]

## 3.1

* By logical communication, we mean that from an application's perspective, it is as if the hosts running the processes were directly connected; in reality, the hosts may be on opposite sides of the planet, connected via numerous routers and a wide range of link types.
  - perspective 观点、角度 [pərˈspektɪv]
  - opposite 相对的、对立的 [ˈɑ:pəzət]
  - via 通过、经过 [ˈvaɪə, ˈviə]
  - numerous 许多、数不清 [ˈnu:mərəs]
  - range 范围、排列 [rendʒ]