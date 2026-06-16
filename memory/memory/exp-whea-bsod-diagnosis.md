---
name: exp-whea-bsod-diagnosis
description: HP笔记本 WHEA 0x124 蓝屏诊断方法：查系统事件日志、解码MCi_STATUS、定位硬件根因
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 8aeb2460-d09c-4679-b06d-ffdffa1cabaf
---

# WHEA 0x124 蓝屏诊断

## 错误现象
HP笔记本（主板8A37，BIOS F.10）蓝屏，错误码 WHEA_UNCORRECTABLE_ERROR (0x124)，伴随持续嗡嗡声（音频缓冲区冻结，非硬件损坏）。

## 诊断方法
1. PowerShell查BugCheck日志：`Get-WinEvent -FilterHashtable @{LogName="System"; Id=1001}`
2. 解码 MCi_STATUS：UC=1 不可纠正，PCC=0 未破坏处理器上下文，错误码0x04850402=内部总线/互联超时
3. 两次蓝屏（间隔9个月）参数完全相同 → 同一硬件组件在特定条件下触发

## 根因
CPU内部总线/互联超时，或VRM瞬态供电不足。不是立刻致命的硬件损坏，特定温度/负载组合触发。

## 修复方向
1. 更新BIOS（当前F.10可能过旧）
2. 用HWiNFO64监控CPU温度电压
3. 如在保联系HP售后

**Why:** 用户电脑HP笔记本反复出现WHEA 0x124蓝屏，需要系统性排查方法。
**How to apply:** 下次蓝屏时先查Event ID 1001获取参数，与已有记录对比判断是否同一根因。
