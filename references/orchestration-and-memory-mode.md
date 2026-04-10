# orchestration-and-memory-mode

## 作用

这份文档提炼自 [agentic-nested-state-machine.opml](agentic-nested-state-machine.opml) 中的：

- 并行分支
- 并行
- 悬置遍历
- 平行分叉
- 分裂
- 异步在哪些场景发挥作用
- 历史记忆编辑工具
- 共享文件编辑工具
- 执行监督
- 共创
- 分支并行 / 分支串行
- 收敛剪枝编辑记忆

当用户不只是要分析结论，而是要设计执行编排、分支策略、共享上下文或记忆剪枝规则时，启用本模式。

## Source Alignment Guard

当当前任务是在对齐原始 `metaPrompt.md` 与 `agentic-nested-state-machine.opml` 时，本模式应优先停留在 source-aligned core：

- `orchestration-plan.json`
- `shared-context-map.json`
- `execution-supervision.json`
- `executor-interface.json`
- `executor-capability-registry.json`
- `memory-pruning.json`
- `writeback-ledger.json`

以下内容属于派生出来的 runtime/provider/governance 运维扩展，不应因为一般性的“并行、共享文件、执行监督、治理”诉求自动激活：

- runtime hook
- runtime event source / schema registry
- consumer compatibility probe
- source-of-truth drift monitor
- scheduler / alert / escalation runtime channel
- provider failover / recovery / stabilization
- threshold governance / external governance source-of-truth

只有当前任务明确涉及真实 runtime 信号、真实 service hook、provider topology、持续 drift monitor 或长期治理运维时，才继续向这些扩展推进。

## 边界读取方式

本模式应按两层读取，而不是把全文当成普通轮次的默认输出清单：

### 第一层：Source-Aligned Orchestration Core

只在任务真的需要以下能力时启用：

- 分支类型设计
- 共享上下文契约
- 执行监督
- 执行接口
- 执行器能力注册
- 记忆剪枝
- 回写留痕

### 第二层：Derived Runtime Operations Extension

只有任务明确进入真实 runtime / service / provider / governance 运维范围时才启用，例如：

- runtime 信号接入
- 外部 service hook
- provider topology
- 持续 drift monitor
- 长期治理运维

### 读取规则

- 本文中出现某个 artifact 名称，不等于当前轮次默认必须产出该 artifact
- 如果当前轮次只需要分支规划、共享上下文、执行监督、记忆剪枝和回写留痕，就停留在第一层
- 只有第一层已经不足以覆盖真实运维问题时，才继续向第二层下钻
- 如果任务仍是 source alignment、skill review 或一般执行编排，不要把第二层 artifact 当成默认义务

## 分支类型

推荐使用以下规范化标签：

- `parallel_worker`
- `parallel_branch`
- `suspended_traversal`
- `parallel_fork`
- `serial_branch`

### 并行分支

特征：

- 同一历史记忆
- 允许修改约束或假设
- 可以进入不同问题空间
- 各分支互不影响

适用：

- 需要从不同约束假设出发探索替代路径
- 对应标签：`parallel_branch`

### 并行

特征：

- 同一历史记忆
- 同一问题定义
- 不改变问题空间
- 只是多个 worker 同时执行不同 todo

适用：

- 同一问题下的并行执行拆分
- 对应标签：`parallel_worker`

### 悬置遍历

特征：

- 暂时搁置当前路径
- 不是永久禁区
- 可回头再进入

适用：

- 当前证据不足，但还不能证明路径无效
- 对应标签：`suspended_traversal`

### 平行分叉

特征：

- 不拥有完整历史记忆
- 未来不一定合并

适用：

- 探索完全不同的问题子空间
- 对应标签：`parallel_fork`

### 分支串行

特征：

- 分支仍然成立
- 但各分支内部必须按严格先后顺序推进

适用：

- 因果链或依赖链不可打断的任务
- 对应标签：`serial_branch`

## 异步与共享上下文

原文明确指出：

- 异步的价值在于并行化执行
- 子节点之间不一定直接通信
- 可以通过共享文件或环境变化来协同

因此当需要轻量协作时，推荐显式记录：

- 谁写什么
- 谁读什么
- 什么内容是共享事实
- 什么内容只是局部假设
- 节点是否通过共享文件或环境变化来协同
- 是否禁止直接消息式通信
- 上下文是“参考资料”还是“可被节点自行重写的记忆”

共享文件不应再被理解成一个“工具”。

更稳定的拆分是：

- `shared_context_contract`
  用 `shared-context-map.json` 记录共享文件、ownership、read_scope、write_scope 与同步说明
- `write_scope_rule`
  用 `execution-supervision.json` 和 `executor-interface.json` 约束谁可以写什么，以及禁止哪些跨分支写入
- `writeback_audit_rule`
  用 `writeback-ledger.json` 记录实际回写、冲突处理、检查点结果与最终共享状态
- `execution_unit_contract`
  用 `executor-interface.json` 的 `execution_units` 取代子 agent 这类身份化叫法
- `worker_scope_contract`
  用 `execution-supervision.json` 的 `worker_scopes` 与接口绑定定义每个执行单元的边界
- `reference_context_binding_rule`
  用 `reference_context_policy` 与 `reference_context_refs` 约束执行单元如何读取上游上下文
- `memory_pruning_rule`
  用 `memory-pruning.json` 记录剪枝、挂起、重启条件与替代摘要
- `writeback_memory_edit_event`
  用 `writeback-ledger.json` 的 `memory_edit_events` 留痕实际发生的记忆替换或剪枝回写
- `replacement_summary_rule`
  用 `replacement_summaries` 保留被剪掉路径的可续接摘要，而不是把历史直接抹掉

## 执行监督

原文对“执行监督”的核心担忧是：

- 规划与执行割裂
- 执行节点只看到结果，不理解上下文

因此若启用执行监督，应至少明确：

- 监督目标
- 执行目标
- 可见上下文范围
- 禁止越界修改的范围
- 分配给谁执行
- 哪些检查点必须回写状态
- 可见性类别
- 权限类别
- 共享文件契约
- 环境观察规则
- todo 如何从上游节点分发下来

## 记忆与剪枝

原文强调：

- 先假定可行
- 连续多轮发现不可行后，再剪掉
- 剪掉时必须保留理由

这比简单删除更像：

- 形成可追溯的“为什么不再采用”
- 以及“未来在什么条件下可以恢复”

## 推荐产物

先按边界顺序读取：

1. 先看第一层 source-aligned orchestration core
2. 只有第一层无法覆盖真实运维范围时，才进入第二层 derived runtime operations extension

### 第一层：Source-Aligned Orchestration Core

### `orchestration-plan.json`

最少应包含：

- `branch_types`
- `branch_class_map`
- `parallel_paths`
- `serial_paths`
- `suspended_paths`
- `merge_policy`
- `shared_context_strategy`
- `coordination_channels`
- `history_visibility_model`
- `branch_merge_expectation`
- `permission_surface`
- `shared_fact_scope`
- `local_hypothesis_scope`

### `shared-context-map.json`

最少应包含：

- `shared_files`
- `ownership`
- `write_scope`
- `read_scope`
- `synchronization_notes`

推荐补充：

- `shared_fact_scope`
- `local_hypothesis_scope`
- `merge_contract`
- `writeback_requirements`

### `execution-supervision.json`

最少应包含：

- `supervision_targets`
- `worker_scopes`
- `assignment_units`
- `context_visibility`
- `visibility_classes`
- `permission_classes`
- `reference_context_policy`
- `shared_file_contracts`
- `environment_observation_rules`
- `direct_message_policy`
- `todo_distribution_policy`
- `handoff_rules`
- `guardrails`
- `prohibited_cross_branch_writes`
- `status_checkpoints`
- `checkpoint_writebacks`
- `escalation_rules`

推荐补充：

- `shared_context_ref`
- `write_scope_bindings`
- `writeback_audit_policy`

这些字段应服务于：

- `assignment_units`
- `worker_scopes`
- `reference_context_policy`

而不是重新发明“子 agent 类型”。

### `executor-interface.json`

最少应包含：

- `execution_units`
- `unit_objectives`
- `todo_packets`
- `reference_context_refs`
- `executor_kind_bindings`
- `required_capability_bindings`
- `adapter_protocol`
- `artifact_io_contracts`
- `visibility_bindings`
- `permission_bindings`
- `writable_targets`
- `prohibited_targets`
- `expected_writebacks`
- `completion_signals`
- `failure_signals`
- `resume_signals`
- `fallback_bindings`
- `checkpoint_hook_bindings`
- `retry_policy`
- `merge_readiness_conditions`

推荐补充：

- `shared_context_ref`
- `write_scope_enforcement`
- `writeback_channel_bindings`

`execution_units`、`reference_context_refs`、`executor_kind_bindings` 与 `required_capability_bindings` 共同承担了过去“子 agent”节点的主要功能语义。

### `executor-capability-registry.json`

最少应包含：

- `registry_schema_version`
- `registry_revision`
- `compatibility_window`
- `compatibility_mode`
- `executor_kinds`
- `capability_matrix`
- `context_window_classes`
- `permission_surfaces`
- `writable_surface`
- `unsupported_actions`
- `fallback_routes`
- `escalation_routes`
- `availability_status`

### 第二层：Derived Runtime Operations Extension

从这里开始的 artifact 目录，只有在真实 runtime / service / provider / governance 运维范围被显式激活时才继续展开。

### `executor-capability-version-policy.json`

最少应包含：

- `current_registry_version`
- `current_schema_version`
- `supported_executor_interface_versions`
- `backward_compatibility_rules`
- `deprecation_rules`
- `compatibility_fallback_rules`
- `migration_entrypoints`
- `version_bump_policy`

### `executor-capability-discovery.json`

最少应包含：

- `discovery_sources`
- `probe_targets`
- `observed_capabilities`
- `observed_availability`
- `observed_context_windows`
- `observed_permission_surfaces`
- `capability_gaps`
- `update_candidates`
- `confidence_per_observation`

### `executor-runtime-hook.json`

最少应包含：

- `hook_targets`
- `signal_sources`
- `probe_channels`
- `expected_runtime_signals`
- `signal_normalization_rules`
- `timeout_policy`
- `writeback_targets`
- `hook_failure_routes`
- `hook_status`

### `runtime-event-source-contract.json`

最少应包含：

- `source_ids`
- `source_types`
- `emitted_events`
- `payload_schema_refs`
- `auth_requirements`
- `delivery_modes`
- `ordering_guarantees`
- `replay_support`
- `normalization_entrypoints`
- `failure_capture_mode`

### `runtime-event-source-registry.json`

最少应包含：

- `source_of_truth`
- `sources`
- `source_classes`
- `current_source_versions`
- `supported_event_schema_versions`
- `auth_profiles`
- `delivery_profiles`
- `source_status`

### `runtime-event-source-service-hook.json`

最少应包含：

- `service_targets`
- `endpoint_profiles`
- `auth_modes`
- `discovery_queries`
- `health_checks`
- `source_registration_fields`
- `writeback_targets`
- `failure_routes`
- `hook_status`

### `runtime-event-schema-version-policy.json`

最少应包含：

- `current_event_schema_version`
- `supported_payload_versions`
- `backward_compatibility_rules`
- `field_coercion_rules`
- `deprecation_rules`
- `replay_compatibility_rules`
- `migration_entrypoints`
- `version_bump_policy`

### `runtime-schema-registry-hook.json`

最少应包含：

- `registry_targets`
- `endpoint_profiles`
- `auth_modes`
- `schema_subjects`
- `version_queries`
- `compatibility_queries`
- `replay_queries`
- `writeback_targets`
- `failure_routes`
- `hook_status`

### `capability-update-ledger.json`

最少应包含：

- `registry_base_version`
- `applied_updates`
- `rejected_updates`
- `fallback_revisions`
- `escalation_revisions`
- `update_rationale`
- `resulting_registry_state`

### `consumer-compatibility-probe.json`

最少应包含：

- `consumer_targets`
- `requested_interface_versions`
- `compatibility_checks`
- `blocked_consumers`
- `downgraded_consumers`
- `probe_evidence`
- `probe_confidence`
- `selected_compatibility_routes`
- `resulting_probe_state`

### `consumer-registry.json`

最少应包含：

- `source_of_truth`
- `consumers`
- `consumer_classes`
- `known_requested_versions`
- `downgrade_preferences`
- `compatibility_requirements`
- `last_seen_state`

### `consumer-registry-service-hook.json`

最少应包含：

- `service_targets`
- `endpoint_profiles`
- `auth_modes`
- `identity_lookup_keys`
- `supported_identity_formats`
- `downgrade_lookup_fields`
- `last_seen_queries`
- `writeback_targets`
- `failure_routes`
- `hook_status`

### `consumer-registry-version-policy.json`

最少应包含：

- `current_consumer_registry_version`
- `consumer_identity_schema_version`
- `supported_identity_formats`
- `backward_compatibility_rules`
- `deprecation_rules`
- `migration_entrypoints`
- `version_bump_policy`

### `consumer-runtime-discovery.json`

最少应包含：

- `discovery_sources`
- `observed_consumers`
- `observed_requested_versions`
- `consumer_identity_rules`
- `confidence_per_consumer`
- `unresolved_consumer_identities`

### `capability-migration-ledger.json`

最少应包含：

- `from_registry_version`
- `to_registry_version`
- `migration_steps`
- `compatibility_checks`
- `deprecated_bindings`
- `compatibility_fallbacks`
- `blocked_consumers`
- `resulting_compatibility_state`

### `runtime-event-schema-migration-ledger.json`

最少应包含：

- `from_event_schema_version`
- `to_event_schema_version`
- `migration_steps`
- `field_mapping_changes`
- `deprecated_event_fields`
- `compatibility_fallbacks`
- `blocked_producers`
- `resulting_event_schema_state`

### `consumer-registry-migration-ledger.json`

最少应包含：

- `from_consumer_registry_version`
- `to_consumer_registry_version`
- `migration_steps`
- `identity_mapping_changes`
- `deprecated_consumer_ids`
- `compatibility_fallbacks`
- `blocked_consumers`
- `resulting_consumer_registry_state`

### `source-of-truth-drift-report.json`

最少应包含：

- `compared_sources`
- `drift_findings`
- `version_drifts`
- `schema_drifts`
- `identity_drifts`
- `severity_per_drift`
- `blocked_routes`
- `suggested_reconciliation`

### `source-of-truth-reconciliation-ledger.json`

最少应包含：

- `applied_reconciliations`
- `rejected_reconciliations`
- `fallback_revisions`
- `escalation_revisions`
- `reconciliation_rationale`
- `resulting_source_of_truth_state`

### `source-of-truth-drift-monitor.json`

最少应包含：

- `monitored_sources`
- `scan_triggers`
- `scan_cadence`
- `comparison_keys`
- `severity_thresholds`
- `monitor_entrypoints`
- `handoff_to_drift_report`
- `pause_conditions`
- `retention_policy`

### `drift-monitor-scheduler.json`

最少应包含：

- `schedule_mode`
- `cadence`
- `trigger_sources`
- `throttle_rules`
- `retry_intervals`
- `maintenance_windows`
- `pause_rules`
- `resume_rules`
- `scheduler_status`

### `drift-scheduler-service-hook.json`

最少应包含：

- `scheduler_targets`
- `endpoint_profiles`
- `auth_modes`
- `trigger_registration_modes`
- `cadence_profiles`
- `pause_resume_controls`
- `status_queries`
- `writeback_targets`
- `failure_routes`
- `hook_status`

### `auto-reconcile-policy.json`

最少应包含：

- `auto_apply_rules`
- `human_review_gates`
- `dry_run_rules`
- `irreversible_blockers`
- `reconciliation_order`
- `rollback_rules`
- `fallback_before_reconcile`
- `stop_conditions`

### `alert-routing-policy.json`

最少应包含：

- `severity_bands`
- `alert_targets`
- `delivery_channels`
- `routing_rules`
- `suppression_rules`
- `aggregation_rules`
- `ack_rules`
- `fallback_channels`

### `alert-delivery-contract.json`

最少应包含：

- `channel_targets`
- `endpoint_profiles`
- `auth_modes`
- `payload_templates`
- `severity_delivery_map`
- `ack_callbacks`
- `retry_profiles`
- `fallback_channels`
- `contract_status`

### `delivery-provider-capability-matrix.json`

最少应包含：

- `providers`
- `channel_support`
- `auth_capabilities`
- `ack_support`
- `retry_support`
- `rate_limits`
- `health_signals`
- `provider_status`

### `provider-health-check.json`

最少应包含：

- `providers`
- `health_endpoints`
- `probe_rules`
- `failure_thresholds`
- `recovery_thresholds`
- `sample_windows`
- `status_mapping`
- `check_status`

### `provider-health-telemetry.json`

最少应包含：

- `providers`
- `telemetry_windows`
- `success_rates`
- `latency_bands`
- `error_rates`
- `jitter_signals`
- `sample_counts`
- `derived_health_state`

### `provider-telemetry-stream-contract.json`

最少应包含：

- `providers`
- `metric_sources`
- `sample_frequencies`
- `aggregation_windows`
- `normalization_rules`
- `missing_sample_policy`
- `late_arrival_policy`
- `writeback_targets`
- `stream_status`

### `channel-failover-policy.json`

最少应包含：

- `route_groups`
- `primary_providers`
- `secondary_providers`
- `failover_triggers`
- `cooldown_rules`
- `stickiness_rules`
- `fallback_order`
- `recovery_rules`

### `circuit-breaker-policy.json`

最少应包含：

- `protected_routes`
- `open_triggers`
- `open_actions`
- `half_open_rules`
- `close_rules`
- `cooldown_windows`
- `recovery_switch_rules`
- `manual_override_rules`

### `circuit-breaker-hysteresis-policy.json`

最少应包含：

- `protected_routes`
- `open_thresholds`
- `close_thresholds`
- `half_open_thresholds`
- `debounce_windows`
- `flapping_rules`
- `suppression_rules`
- `hysteresis_status`

### `anomaly-scoring-policy.json`

最少应包含：

- `monitored_metrics`
- `feature_weights`
- `scoring_formula`
- `severity_mapping`
- `minimum_evidence`
- `smoothing_rules`
- `score_output_fields`
- `policy_status`

### `adaptive-threshold-policy.json`

最少应包含：

- `controlled_thresholds`
- `baseline_windows`
- `update_rules`
- `drift_adjustment_rules`
- `freeze_conditions`
- `rollback_conditions`
- `max_step_change`
- `policy_status`

### `telemetry-baseline-evolution.json`

最少应包含：

- `monitored_metrics`
- `baseline_versions`
- `baseline_windows`
- `seasonality_rules`
- `drift_triggers`
- `update_frequency`
- `freeze_conditions`
- `activation_status`

### `human-escalation-workflow.json`

最少应包含：

- `escalation_levels`
- `review_gates`
- `responder_roles`
- `response_slas`
- `fallback_actions`
- `approval_requirements`
- `closure_conditions`
- `escalation_status`

### `human-escalation-channel.json`

最少应包含：

- `channel_targets`
- `intake_modes`
- `assignment_rules`
- `ack_slas`
- `closure_callbacks`
- `fallback_channels`
- `channel_status`

### `provider-recovery-switch-ledger.json`

最少应包含：

- `health_check_cycles`
- `breaker_transitions`
- `recovered_providers`
- `switch_back_events`
- `suppressed_switches`
- `final_breaker_state`
- `resulting_provider_state`

### `recovery-canary-policy.json`

最少应包含：

- `canary_routes`
- `initial_traffic_split`
- `ramp_stages`
- `observation_metrics`
- `success_thresholds`
- `rollback_triggers`
- `promotion_rules`
- `canary_status`

### `threshold-adaptation-ledger.json`

最少应包含：

- `evaluated_cycles`
- `anomaly_scores`
- `applied_threshold_updates`
- `frozen_thresholds`
- `rejected_updates`
- `rollback_events`
- `resulting_threshold_state`

### `anomaly-model-recalibration.json`

最少应包含：

- `recalibration_triggers`
- `affected_metrics`
- `old_feature_weights`
- `new_feature_weights`
- `feature_replacements`
- `validation_checks`
- `rollback_rules`
- `resulting_model_state`

### `threshold-governance-workflow.json`

最少应包含：

- `governance_levels`
- `approval_gates`
- `override_roles`
- `audit_requirements`
- `freeze_rules`
- `activation_order`
- `rollback_authority`
- `workflow_status`

### `threshold-governance-ledger.json`

最少应包含：

- `approval_events`
- `rejected_changes`
- `frozen_controls`
- `manual_overrides`
- `audit_records`
- `rollback_actions`
- `resulting_governance_state`

### `baseline-governance-service-hook.json`

最少应包含：

- `service_targets`
- `endpoint_profiles`
- `auth_modes`
- `baseline_queries`
- `freeze_queries`
- `version_queries`
- `writeback_targets`
- `failure_routes`
- `hook_status`

### `anomaly-model-registry.json`

最少应包含：

- `registry_targets`
- `model_versions`
- `feature_sets`
- `feature_weights`
- `calibration_status`
- `compatibility_windows`
- `rollback_entrypoints`
- `registry_status`

### `threshold-policy-registry.json`

最少应包含：

- `registry_targets`
- `threshold_versions`
- `controlled_thresholds`
- `approval_status`
- `activation_windows`
- `freeze_states`
- `rollback_entrypoints`
- `registry_status`

### `governance-sync-ledger.json`

最少应包含：

- `compared_governance_sources`
- `sync_events`
- `accepted_updates`
- `rejected_updates`
- `frozen_items`
- `audit_deltas`
- `resulting_governance_sync_state`

### `governance-source-drift-report.json`

最少应包含：

- `compared_governance_sources`
- `drift_findings`
- `baseline_drifts`
- `model_drifts`
- `threshold_policy_drifts`
- `severity_per_drift`
- `blocked_governance_routes`
- `suggested_reconciliation`

### `governance-source-reconciliation-ledger.json`

最少应包含：

- `applied_reconciliations`
- `rejected_reconciliations`
- `fallback_revisions`
- `escalation_revisions`
- `reconciliation_rationale`
- `resulting_governance_source_state`

### `governance-approval-channel.json`

最少应包含：

- `channel_targets`
- `intake_modes`
- `approval_callbacks`
- `rejection_callbacks`
- `escalation_routes`
- `sla_profiles`
- `closure_callbacks`
- `channel_status`

### `governance-review-scheduler.json`

最少应包含：

- `schedule_mode`
- `cadence`
- `trigger_sources`
- `throttle_rules`
- `retry_intervals`
- `maintenance_windows`
- `pause_rules`
- `resume_rules`
- `scheduler_status`

### `governance-alert-routing-policy.json`

最少应包含：

- `severity_bands`
- `alert_targets`
- `delivery_channels`
- `routing_rules`
- `suppression_rules`
- `aggregation_rules`
- `ack_rules`
- `fallback_channels`

### `governance-review-cadence.json`

最少应包含：

- `review_cycles`
- `review_windows`
- `escalation_windows`
- `freeze_windows`
- `recheck_rules`
- `overdue_rules`
- `review_priority_rules`
- `cadence_status`

### `governance-review-ops-ledger.json`

最少应包含：

- `review_cycles`
- `triggered_reviews`
- `delivered_alerts`
- `approval_events`
- `skipped_reviews`
- `escalations`
- `next_review_plan`

### `governance-provider-capability-matrix.json`

最少应包含：

- `providers`
- `channel_support`
- `auth_capabilities`
- `ack_support`
- `retry_support`
- `rate_limits`
- `health_signals`
- `provider_status`

### `governance-channel-failover-policy.json`

最少应包含：

- `route_groups`
- `primary_providers`
- `secondary_providers`
- `failover_triggers`
- `cooldown_rules`
- `stickiness_rules`
- `fallback_order`
- `recovery_rules`

### `governance-delivery-failover-ledger.json`

最少应包含：

- `failover_events`
- `trigger_reasons`
- `attempted_providers`
- `selected_providers`
- `reverted_providers`
- `dropped_messages`
- `resulting_delivery_state`

### `delivery-failover-ledger.json`

最少应包含：

- `failover_events`
- `trigger_reasons`
- `attempted_providers`
- `selected_providers`
- `reverted_providers`
- `dropped_messages`
- `resulting_delivery_state`

### `drift-scan-ledger.json`

最少应包含：

- `scan_cycles`
- `trigger_events`
- `detected_drifts`
- `actions_taken`
- `skipped_actions`
- `escalations`
- `next_scan_plan`

### 第一层闭环补充：Memory Pruning And Writeback

下面两个 artifact 虽然出现在文档尾部，但仍然属于第一层 source-aligned orchestration core 的闭环产物，而不是第二层运维扩张产物。

### `memory-pruning.json`

最少应包含：

- `pruned_paths`
- `suspended_paths`
- `pruning_reasons`
- `retained_summaries`
- `reactivation_conditions`
- `prune_after_failed_rounds`
- `deletion_scope`
- `memory_edit_targets`
- `replacement_summaries`

这些字段共同承担了过去“历史记忆编辑工具”的主要语义：

- `memory_edit_targets`
  指向哪些历史上下文或路径被替换
- `replacement_summaries`
  指向替换后保留下来的可续接摘要
- `reactivation_conditions`
  指向何时允许恢复被挂起或被替换的路径

### `writeback-ledger.json`

最少应包含：

- `observed_writebacks`
- `environment_observation_events`
- `checkpoint_results`
- `merge_decisions`
- `conflict_events`
- `memory_edit_events`
- `deferred_updates`
- `final_shared_state`

若本轮发生了记忆替换或剪枝回写，推荐补充：

- `memory_pruning_ref`
- `replacement_summary_refs`

推荐补充：

- `source_shared_context_ref`
- `audited_contracts`
- `unresolved_merge_risks`

## 默认规则

- 本文列出的 artifact 是边界化目录，不是普通轮次默认全量清单
- 如果第一层已经足以支撑当前轮次，就停止，不继续向第二层扩张
- 未出现真实 runtime / service / provider / governance 运维需求时，不要继续生成第二层 artifact
- 第二层中的 “应生成 / 应补齐” 都应理解为条件成立后的局部义务，而不是默认义务
- 不要过早硬剪枝
- 不可逆删除必须慎用
- 对低置信路径优先挂起，不要立刻永久删除
- 如果分支只是执行差异而不是问题空间差异，优先视为并行而不是并行分支
- 如果挂起路径未来仍可能恢复，必须写入 `memory-pruning.json`，不能只在自然语言里口头说明
- 如果节点通过共享文件协同，默认禁止直接互发消息，除非另有显式授权
- 如果共享文件协同已显式存在，则应先生成 `shared-context-map.json`，再让 `execution-supervision.json` 和 `executor-interface.json` 细化它
- `shared-context-map.json` 是 planning source；`execution-supervision.json` 与 `executor-interface.json` 可以细化，但不应改写其中的 ownership、read_scope、write_scope
- 执行节点看到的上游材料默认应视为 `reference_context`，而不是它自己可随意改写的记忆
- 不要再用“子 agent”作为默认 contract 名称；默认应使用 `execution_unit`、`worker_scope` 与 `reference_context` 这些结构语义
- 不要再用“历史记忆编辑工具”作为默认 contract 名称；默认应使用 `memory_pruning`、`memory_edit_events` 与 `replacement_summaries` 这些结构语义
- 如果存在共享文件回写、环境观察或检查点写回，则应生成 `writeback-ledger.json`，把实际回写和最终合并状态留痕
- 如果已经进入执行监督层，则应生成 `executor-interface.json`，把 todo 分发和 reference_context 边界压成显式接口
- 如果希望 executor-interface 能被真实执行器消费，则必须继续把执行器类型、输入输出契约、失败信号、恢复信号和检查点钩子压成显式字段
- 如果不同执行器类型的能力并不相同，则应生成 `executor-capability-registry.json`，并为能力缺口提供 fallback_routes 或 escalation_routes
- 如果执行器能力、可用性或权限曲面会变化，则应生成 `executor-capability-discovery.json`
- 如果 discovery 依赖 runtime 信号或外部探针，则应生成 `executor-runtime-hook.json`
- 如果 runtime hook 依赖真实事件源契约，则应生成 `runtime-event-source-contract.json`
- 如果 runtime event source 本身需要注册、分类或版本覆盖，则应生成 `runtime-event-source-registry.json`
- 如果 runtime event source 通过真实 service 暴露，则应生成 `runtime-event-source-service-hook.json`
- 如果 runtime event schema 会演化，则应生成 `runtime-event-schema-version-policy.json`
- 如果 schema registry 通过真实 service 暴露，则应生成 `runtime-schema-registry-hook.json`
- 如果 discovery 结果会修改注册表或 fallback 路由，则应生成 `capability-update-ledger.json`
- 如果 registry 会持续演化，则应补齐 `executor-capability-version-policy.json`
- 如果 update 造成版本变化、弃用或兼容性破坏，则应补齐 `capability-migration-ledger.json`
- 如果兼容判断依赖实际 consumer 请求或 probe 结果，则应补齐 `consumer-compatibility-probe.json`
- 如果 compatibility 判断依赖 consumer source-of-truth 或 runtime consumer 识别，则应补齐 `consumer-registry.json` 与 `consumer-runtime-discovery.json`
- 如果 consumer source-of-truth 通过真实 service 暴露，则应补齐 `consumer-registry-service-hook.json`
- 如果 consumer source-of-truth 本身会版本化或迁移，则应补齐 `consumer-registry-version-policy.json`
- 如果 event schema 或 consumer registry 发生版本迁移，则应分别补齐 `runtime-event-schema-migration-ledger.json` 与 `consumer-registry-migration-ledger.json`
- 如果 service/source registry/runtime observation 之间出现 drift，则应补齐 `source-of-truth-drift-report.json`
- 如果 drift 进入修复路径，则应补齐 `source-of-truth-reconciliation-ledger.json`
- 如果需要持续监测 drift，则应补齐 `source-of-truth-drift-monitor.json`
- 如果 drift monitor 需要调度运行，则应补齐 `drift-monitor-scheduler.json`
- 如果 drift monitor 需要接入真实 scheduler，则应补齐 `drift-scheduler-service-hook.json`
- 如果允许自动修复 drift，则应补齐 `auto-reconcile-policy.json`
- 如果 drift 需要告警分发，则应补齐 `alert-routing-policy.json`
- 如果 drift 告警需要接入真实投递通道，则应补齐 `alert-delivery-contract.json`
- 如果告警或升级依赖多个 provider/多个通道，则应补齐 `delivery-provider-capability-matrix.json` 与 `channel-failover-policy.json`
- 如果 provider failover 依赖健康状态，则应补齐 `provider-health-check.json`
- 如果 provider 健康需要基于遥测窗口判断，则应补齐 `provider-health-telemetry.json`
- 如果 provider 健康依赖持续遥测流，则应补齐 `provider-telemetry-stream-contract.json`
- 如果 provider 需要熔断/恢复切回，则应补齐 `circuit-breaker-policy.json`
- 如果 provider 恢复需要防抖和回差控制，则应补齐 `circuit-breaker-hysteresis-policy.json`
- 如果恢复判断依赖异常评分，则应补齐 `anomaly-scoring-policy.json`
- 如果阈值需要自适应，则应补齐 `adaptive-threshold-policy.json`
- 如果 drift 需要人工审核闸门，则应补齐 `human-escalation-workflow.json`
- 如果人工审核需要接入真实升级通道，则应补齐 `human-escalation-channel.json`
- 如果告警或升级发生 provider/channel failover，则应补齐 `delivery-failover-ledger.json`
- 如果 provider 发生恢复切回，则应补齐 `provider-recovery-switch-ledger.json`
- 如果 provider 恢复切回需要金丝雀放量，则应补齐 `recovery-canary-policy.json`
- 如果阈值发生自适应更新、冻结或回滚，则应补齐 `threshold-adaptation-ledger.json`
- 如果长期治理依赖外部 baseline service，则应补齐 `baseline-governance-service-hook.json`
- 如果长期治理依赖外部 anomaly model registry，则应补齐 `anomaly-model-registry.json`
- 如果长期治理依赖外部 threshold policy registry，则应补齐 `threshold-policy-registry.json`
- 如果外部治理系统与本地治理状态发生同步，则应补齐 `governance-sync-ledger.json`
- 如果外部治理 source 与本地治理状态发生 drift，则应补齐 `governance-source-drift-report.json`
- 如果治理 drift 进入修复路径，则应补齐 `governance-source-reconciliation-ledger.json`
- 如果长期治理需要接入外部审批通道，则应补齐 `governance-approval-channel.json`
- 如果长期治理需要持续审查调度，则应补齐 `governance-review-scheduler.json` 与 `governance-review-cadence.json`
- 如果治理 drift 需要专用告警路由，则应补齐 `governance-alert-routing-policy.json`
- 如果治理审查已实际运行，则应补齐 `governance-review-ops-ledger.json`
- 如果治理告警或审批依赖多个 provider/多个通道，则应补齐 `governance-provider-capability-matrix.json` 与 `governance-channel-failover-policy.json`
- 如果治理告警或审批发生 provider/channel failover，则应补齐 `governance-delivery-failover-ledger.json`
- 如果 drift monitor 已经执行扫描，则应补齐 `drift-scan-ledger.json`
