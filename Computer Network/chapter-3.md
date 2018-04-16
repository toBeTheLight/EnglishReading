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

# 3.1

* By logical communication, we mean that from an application's perspective, it is as if the hosts running the processes were directly connected; in reality, the hosts may be on opposite sides of the planet, connected via numerous routers and a wide range of link types.
  - perspective 观点、角度 [pərˈspektɪv]
  - opposite 相对的、对立的 [ˈɑ:pəzət]
  - via 通过、经过 [ˈvaɪə, ˈviə]
  - numerous 许多、数不清 [ˈnu:mərəs]
  - range 范围、排列 [rendʒ]

* Application processes use the logical communication provided by the transport layer to send messages to each other, free from the worry of the details of the physical infrastructure used to carry these message.
  - physical [ˈfɪzɪkəl]
  - infrastructure 基础设置 [ˈɪnfrəˌstrʌktʃɚ]

* Figure 3.1 illustrates the notion of ligical communication.
  - figure 图表、数字、人物 [ˈfɪgjər]
  - notion 见解、概念 [ˈnoʊʃn]

* On the sending side, the transport layer converts the messages it receives from a sending application process into transport-layer packets, known as transport-layer segments in Internet terminology.
  - converts 转变 [kənˈvɜ:rt]
  - receive [rɪˈsiv]
  - segment 部分、分段、段 [ˈsɛɡmənt]
  - terminology 专用名词 [ˌtɜ:rməˈnɑ:lədʒi]

* The transport layer then passes the segment to the network layer at the sending end system, where the segment is encapsulated within network-layer packet (a datagram) and sent to the destination.
  - encapsulate 封住、概述 [ɛnˈkæpsəˌlet]
  - datagram 数据报 ['detə,græm]
  - destination 终点 [,dɛstɪ'neʃən]

* On the receiving side, the network-layer extracts the transport-layer segment from the datagram and passes the segment up to transport layer.
  - extract 提取 ['ɛkstrækt]

## 3.1.1 

* Recall that the transport layer lies just above the network layer in the protocol stack.
  - recall 回想起、回忆 ['rikɔl]

* This distinction is subtle but important. Let‘s examine this distinction with the aid of a household analogy.
  - distinction 区别 [dɪ'stɪŋkʃən]
  - subtle 微妙的、狡猾的 ['sʌtl]
  - aid 帮助、助手、援助 [ed]
  - household 家庭 ['haʊshold]
  - analogy 类比 [ə'nælədʒi]

* The kids in the two households love to write to each other--each kid writes each cousin every week, with each letter delivered by the traditional postal service in a separate envelope.
  - cousin 堂（表）兄弟姐妹 ['kʌzn]
  - traditional 传统的 [trə'dɪʃənl]
  - postal 邮局的 ['postl]
  - separate 分离的 [(v) sɛpəˌret;(adj) sɛprɪt]
  - envelope 信封、包层 ['envələʊp; 'ɒn-]

* They are not involved, for example, in sorting mail in any intermediate mail center or in moving mail from one mail center to another.
  - involve 参与、涉及 [ɪnˈvɑ:lv]
  - intermediate 中间的 [ˌɪntərˈmi:diət]

* Within an end system, a transport protocol moves messages from application processes to the network edge (that is, the network layer) and vice versa, but it doesn't have any say about how the messages are moved within the network core.
  - edge 边缘 [ɛdʒ]
  - network edge 网络接收层
  - and vice versa 反之亦然
  - core [kɔr, kor]

* Intermediate routers neither act on, nor recognize, any information that the transport layer may have added to the application messages.
  - recognize 识别承认 [ˈrɛkəɡˌnaɪz]

* In a similar manner, the services that a transport protocol can provide are often constrained by the service model of the underlying network-layer protocol.
  - manner 方法、方式、样子 [ˈmænɚ]
  - constraine 受限 [kənˈstreɪnd]
  - underlying 潜在、底层 [ˌʌndərˈlaɪɪŋ]

* If the network-layer protocol cannot provide delay or bandwidth guarantees for transport-layer segments sent between hosts, then the transport-layer protocol cannot provide delay or bandwidth guarantees for application messages sent between processes.
  - bandwidth 带宽 [ˈbændˌwɪdθ, -ˌwɪθ]
  - guarantee 保证 [ˌɡærənˈti]

* For example, as we'll see in this chapter, a transport protocol can offer reliable data transfer service to an application even when the underlying network protocol is unreliable, that is, even when the network protocol loses, garbles, or duplicates packets.
  - garble 歪曲、篡改 [ˈɡɑrbəl]
  - duplicate 复制 [ˈdu:plɪkeɪt]

* As another example (which we'll explore in Chapter 8 when we discuss network security), a transport protocol can use encryption to guarantee that application messages are not read by intruders, even when the network layer cannot guarantee the confidentiality of transport-layer segments.
  - security 安全、保证 [səˈkjʊrəti]
  - encryption 加密 [ɪn'krɪpʃn]
  - intruder 干扰者、闯入者 [ɪn'tru:dər]
  - confidentiality 机密性 [ˌkɑ:nfɪˌdenʃiˈæləti]

## 3.1.2

* Recall that the Internet, and more generally a TCP/IP network, makes available two distinct transport-alyer protocols to the application layer.
  - generally 通常 [ˈdʒɛnərəli]
  - distinct 明显的、有区别的 [dɪˈstɪŋkt] 

* But this same Internet literature also uses the term datagram for the network-layer packet! For an introductory book on computer networking such as this, we believe that it is less confusing to refer to both TCP and UDP packets as segments, and reserve the term datagram for the network-layer packet.
  - literature 文学作品、著作 [ˈlɪtərəˌtʃʊr, -tʃɚ]
  - term 术语 [tɜ:rm]
  - introductory 引导的、介绍的 [ˌɪntrəˈdʌktəri]
  - confuse 使困惑 [kənˈfjuz]
  - reserve 保留 [rɪˈzɜ:rv]

* Having taken a glimpse at the IP service model, let's now summarize the service models provided by UDP and TCP.
  - glimpse 一瞥 [ɡlɪmps]
  - summarize 总结 [ˈsʌməˌraɪz]

* Extending host-to-host delivery to process-to-process delivery is called transport-layer multiplexing and demultiplexing.
  - multiplexing 多路复用 ['mʌltɪpleksɪŋ]
  - demultiplexing 多路分解 [dɪmʌltɪp'leksɪŋ]

* UDP and TCP also provide integrity checking by including error-detection fields in their segments' headers. These two minimal transport-layer services——process-to-process data delivery and error checking——are the only two services that UDP provides!
  - integrity 完整、健全、正直 [ɪnˈtɛɡrɪti]
  - detection 检测 [dɪˈtɛkʃən]
  - minimal 极小的、最小的 [ˈmɪnəməl]

* TCP congestion control prevents any one TCP connection from swamping the links and routers between communicating hosts with an excessive amount of traffic.
  - swamp 淹没 [swɑ:mp]
  - excessive 过多的 [ɪkˈsɛsɪv]
  - amount 量、总和 [əˈmaʊnt]
  
* TCP strives to give each connection traversing a congested link an equal share of the link bandwidth.
  - strive 力争 [straɪv]
  - traverse 通过 [trəˈvɜ:rs]

# 3.2

* Because at any given time there can be more than one socket in the receiving host, each socket has a unique identifier.
  - unique 独特的 [juˈnik]
  - identifier 识别码 [aɪ'dɛntɪfaɪɚ]

* Now let's consider how a receiving host directs an incoming transport-layer segment to the appropriate socket.
  - incoming 进来的
  - appropriate 合适 [əˈproʊpriət]

* Each transport-layer segment has a set of fields in the segment for this purpose.
  - purpose 目的 [ˈpɜ:rpəs]

* The job of gathering data chunks at the source host from different socket, encapsulating each data chunk with header information (that will be later be used in demultiplexing) to create segment, and passing the segments to the network layer is called multiplexing.
  - gather 收集、采集 [ˈɡæðɚ]

* When Bill receives a batch of mail from the mail carrier, he performs a demultiplexing operation by observing to whom the letters are addressed and then hand delivering the mail to his brothers and sisters.
  - batch 一批 [bætʃ]
  - perform 执行 [pərˈfɔ:rm]
  - operation 操作 [ˌɑ:pəˈreɪʃn]
  - observe 观察 [əbˈzɜ:rv]

* Typically, the client side of the application lets the transport layer automatically (and transparently) assign the port number, whereas the server side of the application assigns a specific port number.
  - typically 通常的 [ˈtɪpɪklɪ]
  - automatically 自动的、无意识的 [ˌɔtəˈmætɪkl:ɪ]
  - assign 分配、归属 [əˈsaɪn]
  - whereas 然而、反之 [ˌwerˈæz]
  - specific 明确的 [spɪˈsɪfɪk]

* The server host may support many simultaneous TCP sockets, with each socket attached to a process, and with each socket idenitified by its own four-tuple.
  - simultaneous 同时的 [ˌsaɪmlˈteɪniəs]
  - attached 固定从属 [əˈtætʃ]
  - tuple 元组 [tʌpl]
  - idenitify 识别 [aɪˈdɛntəˌfaɪ]

* It's instructive to say a few additional words about Web servers and how they use port numbers.
  - instructive 有益的、教育的 [ɪnˈstrʌktɪv]
  - additional 补充的 [ə'dɪʃənl]

* The server distinguishes the segments from the different clients using source IP addresses and source port numbers.
  - distinguish 区分、辨别 [dɪˈstɪŋɡwɪʃ] 

* If the client and server are using persistent HTTP, then throughout the duration of the persistent connection the client and server exchange HTTP messages via the same server socket.
  - persistent 持续的、坚持的 [pərˈsɪstənt]
  - throughout 在...期间、遍布 [θruˈaʊt]
  - duration 持续期间 [duˈreɪʃn]
  - exchange 交换 [ɪksˈtʃendʒ]

* This frequent creating and closing of sockets can severely impact the performance of a busy Web server (although a number of operating system tricks can be used to mitigate the problem).
  - frequent 频繁 [ˈfrikwənt]
  - severely 严重的 [səˈvɪrlɪ]
  - impact 影响、冲击 [ˈɪmˌpækt]
  - trick 戏法、技巧 [trɪk]
  - mitigate 使缓和、减轻 [ˈmɪtˌɪɡet]

# 3.3

* To motivate our discussion about UDP, suppose you were interested in designing a no-frills, bare-bones transport prorocol.
  - motivate 促使、刺激 [ˈmoʊtɪveɪt]
  - frill 装饰 [frɪl]
  - bare-bones 皮包骨头、极简的 [ber] [boʊnz]

* You might first consider using a vacuous transport protocol.
  - vacuous 空虚、无聊、愚蠢的 [ˈvækjuəs]

* TCP, on the other hand, has a congestion-control mechanism that throttles the transport-layer TCP sender when one or more links between the source and destination hosts become excessively congested.
  - mechanism 机制、机理 [ˈmɛkəˌnɪzəm]
  - throttle 遏制、压制 [ˈθrɑ:tl]

* TCP will also continue to resend a segment until the receipt of the segment has been acknowledged by the destination, regardless of how long reliable delivery takes.
  - receipt 收据、发票 [rɪˈsit]
  - acknowledged 公认、承认 [ək'nɒlɪdʒd]
  - regardless 不管怎样、不顾后果 [rɪˈgɑ:rdləs]

* Although commonly done today, running multimedia applications over UDP is controversial.
  - multimedia 多媒体 [ˌmʌltiˈmidiə]
  - controversial 有争议的 [ˌkɑ:ntrəˈvɜ:rʃl]

* There would be so much packet overflow at routers that very few UDP packets would successfully traverse the source-to-destination path.
  - overflow 溢出
  - traverse 穿过 [trəˈvɜ:rs]

* Moreover, the high loss rates induced by the uncontrolled UDP senders would cause the tcp sender (which, as we'll see, do decrease their sending rates in the face of congestion) to dramatically decrease their rates.
  - induce 引起 [ɪnˈdu:s]
  - decrease 减少 [dɪˈkris]
  - dramatically 引人注目的 [drəˈmætɪkl:ɪ]

* That is, application processes can communicate reliably without being subjected to the transmission-rate constraints imposed by TCP’s congestion-control mechanism.
  - subject 屈从 [ˈsʌbdʒekt]
  - constraint 约束、限制 [kənˈstrent]
  - impose 强加 [ɪmˈpoʊz]
  - mechanism 机制 [ˈmɛkəˌnɪzəm]

## 3.3.1

* The checksum is used by the receiving host to check whether error have been introduced into the segment. In truth, the checksum is also calculated over a few of the fields in the IP header in addition to the UDP segment.
  - checksum 校验 [ˈtʃeksʌm]
  - introduce 引进 [ˌɪntrəˈdu:s]
  - calculate 计算、估算 [ˈkælkjəˌlet]
  - addition 增加 [əˈdɪʃən]
  - in addition to 除了

## 3.3.2

The checksum is used to determine whether bits within the UDP segment have been altered (for example, by noise in the links or while stored in a router) as it moved from source to destination.
  - determine 确定 [dɪˈtɜ:rmɪn]
  - alter 改变 [ˈɔltɚ]

* UDP at the sender side performs the 1s complement of the sum of all the 16-bit words in the segment, with any overflow encountered during the sum being wrapped around.
  - complement 补码 [ˈkɑ:mplɪment]
  - encounter 遭遇 [ɛnˈkaʊntɚ]

# 3.4

* This is appropritate since the problem of implementing reliable data transfer occurs not only at the transport layer.
  - appropritate 适当的 [əˈprəʊpriət]
  - implementing 事实、执行 [ˈɪmpləmənt]
  - occur 发出、出现 [əˈkɚ]

* Indeed, if one had to identify a "top-ten" list of fundamentally  important problems in all of networking, this would be a candidate to lead the list.
  - Indeed 确实 [ɪnˈdid]
  - identify 确定、认出 [aɪˈdɛntəˌfaɪ]
  - candidate 报考者、候选 [ˈkændɪˌdet]

* In the next section we'll examine TCP and show, in particular, that TCP exploits many of the principles that we are about to describe.
  - exploit 开拓、开采 [ɪkˈsplɔɪt]

* This is precisely the service model offered by TCP to the Internet applications that invoke it.
  - precise 精密、精确的 [prɪˈsaɪs]

* It is the responsibility of a reliable data transfer protocol to implement this service abstraction.
  - abstraction 抽象 [æbˈstrækʃən]

* In this section, we will incrementally develop the sender and receiver sides of a reliable data transfer protocol, considering increasingly complex models of the underlaying channel.
  - incrementally 逐渐地 [,inkri'məntəli]
  - complex [kəmˈpleks]

* In this section we consider only the case of unidirectional data transfer, that is, data transfer from the sending to the receiving side. The case of reliable bidirectional data transfer is conceptually no more difficult but considerably more tedious to explain.
  - unidirectional 单向的 [ˌju:nɪdə'rekʃənəl]
  - bidirectional 双向的 [ˌbaɪdɪˈrɛkʃənəl]
  - conceptually 概念地 [kən'septʃʊrlɪ]
  - tedious 昂长的 [ˈtidiəs]
