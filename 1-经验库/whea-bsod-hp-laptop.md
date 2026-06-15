# WHEA 0x124 蓝屏诊断
- 日期: 2026-06-15
- 项目: 系统
- 现象: HP 笔记本黑屏蓝屏，停止码 WHEA_UNCORRECTABLE_ERROR (0x124)，风扇狂转+持续嗡嗡声
- 根因: CPU内部总线/互联超时，特定温度/负载触发，McSTATUS=0xBA00000004850402
- 修复: 查事件日志 `Get-WinEvent -FilterHashtable @{LogName="System"; Id=1001}`；两次蓝屏隔9个月，同参数→硬件暗病；更新BIOS+HWiNFO64监控
