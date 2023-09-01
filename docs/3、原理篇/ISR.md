# ISR
ISR是Broker维护的一个“可靠的follower列表”。


AR：分区中所有副本称为 AR
ISR：所有与主副本保持一定程度同步的副本（包括主副本）称为 ISR(In-SyncReplicas)
OSR：与主副本滞后过多的副本组成 OSR(Out-SyncReplicas)

Leader 会维护一个与自己基本保持同步的Replica列表，该列表称为ISR，每个Partition都会有一个ISR，而且是由Leader动态维护。
所谓动态维护，就是说如果一个Follower比一个Leader落后太多，或者超过一定时间未发起数据复制请求，则Leader将其从ISR中移除。
当ISR中所有Replica都向Leader发送ACK（Acknowledgement确认）时，Leader才commit。


