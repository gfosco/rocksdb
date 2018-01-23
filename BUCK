REPO_PATH = "./"

BUCK_BINS = "buck-out/gen/" + REPO_PATH

TEST_RUNNER = REPO_PATH + "buckifier/rocks_test_runner.sh"

rocksdb_compiler_flags = [
    "-fno-builtin-memcmp",
    "-DROCKSDB_PLATFORM_POSIX",
    "-DROCKSDB_LIB_IO_POSIX",
    "-DROCKSDB_FALLOCATE_PRESENT",
    "-DROCKSDB_MALLOC_USABLE_SIZE",
    "-DROCKSDB_RANGESYNC_PRESENT",
    "-DROCKSDB_SCHED_GETCPU_PRESENT",
    "-DROCKSDB_SUPPORT_THREAD_LOCAL",
    "-DOS_LINUX",
    # Flags to enable libs we include
    #"-DSNAPPY",
    #"-DZLIB",
    #"-DBZIP2",
    #"-DLZ4",
    #"-DZSTD",
    #"-DGFLAGS=gflags",
    "-DNUMA",
    #"-DTBB",
    #"-DHAVE_SSE42",
    "-std=c++11",
]

rocksdb_external_deps = [
    ("bzip2", None, "bz2"),
    ("snappy", None, "snappy"),
    ("zlib", None, "z"),
    ("gflags", None, "gflags"),
    ("lz4", None, "lz4"),
    ("zstd", None),
    ("tbb", None),
    ("numa", None, "numa"),
    ("googletest", None, "gtest"),
]

rocksdb_preprocessor_flags = [
    # Directories with files for #include
    "-I" + REPO_PATH + "include/",
    "-I" + REPO_PATH,
    "-I" + REPO_PATH + "third-party/gtest-1.7.0/fused-src/",
]


cxx_library(
    name = "rocksdb_lib",
    srcs = [
        "cache/clock_cache.cc",
        "cache/lru_cache.cc",
        "cache/sharded_cache.cc",
        "db/builder.cc",
        "db/c.cc",
        "db/column_family.cc",
        "db/compacted_db_impl.cc",
        "db/compaction.cc",
        "db/compaction_iterator.cc",
        "db/compaction_job.cc",
        "db/compaction_picker.cc",
        "db/compaction_picker_universal.cc",
        "db/convenience.cc",
        "db/db_filesnapshot.cc",
        "db/db_impl.cc",
        "db/db_impl_compaction_flush.cc",
        "db/db_impl_debug.cc",
        "db/db_impl_experimental.cc",
        "db/db_impl_files.cc",
        "db/db_impl_open.cc",
        "db/db_impl_readonly.cc",
        "db/db_impl_write.cc",
        "db/db_info_dumper.cc",
        "db/db_iter.cc",
        "db/dbformat.cc",
        "db/event_helpers.cc",
        "db/experimental.cc",
        "db/external_sst_file_ingestion_job.cc",
        "db/file_indexer.cc",
        "db/flush_job.cc",
        "db/flush_scheduler.cc",
        "db/forward_iterator.cc",
        "db/internal_stats.cc",
        "db/log_reader.cc",
        "db/log_writer.cc",
        "db/malloc_stats.cc",
        "db/managed_iterator.cc",
        "db/memtable.cc",
        "db/memtable_list.cc",
        "db/merge_helper.cc",
        "db/merge_operator.cc",
        "db/range_del_aggregator.cc",
        "db/repair.cc",
        "db/snapshot_impl.cc",
        "db/table_cache.cc",
        "db/table_properties_collector.cc",
        "db/transaction_log_impl.cc",
        "db/version_builder.cc",
        "db/version_edit.cc",
        "db/version_set.cc",
        "db/wal_manager.cc",
        "db/write_batch.cc",
        "db/write_batch_base.cc",
        "db/write_controller.cc",
        "db/write_thread.cc",
        "env/env.cc",
        "env/env_chroot.cc",
        "env/env_encryption.cc",
        "env/env_hdfs.cc",
        "env/env_posix.cc",
        "env/io_posix.cc",
        "env/mock_env.cc",
        "memtable/alloc_tracker.cc",
        "memtable/hash_cuckoo_rep.cc",
        "memtable/hash_linklist_rep.cc",
        "memtable/hash_skiplist_rep.cc",
        "memtable/skiplistrep.cc",
        "memtable/vectorrep.cc",
        "memtable/write_buffer_manager.cc",
        "monitoring/histogram.cc",
        "monitoring/histogram_windowing.cc",
        "monitoring/instrumented_mutex.cc",
        "monitoring/iostats_context.cc",
        "monitoring/perf_context.cc",
        "monitoring/perf_level.cc",
        "monitoring/statistics.cc",
        "monitoring/thread_status_impl.cc",
        "monitoring/thread_status_updater.cc",
        "monitoring/thread_status_updater_debug.cc",
        "monitoring/thread_status_util.cc",
        "monitoring/thread_status_util_debug.cc",
        "options/cf_options.cc",
        "options/db_options.cc",
        "options/options.cc",
        "options/options_helper.cc",
        "options/options_parser.cc",
        "options/options_sanity_check.cc",
        "port/port_posix.cc",
        "port/stack_trace.cc",
        "table/adaptive_table_factory.cc",
        "table/block.cc",
        "table/block_based_filter_block.cc",
        "table/block_based_table_builder.cc",
        "table/block_based_table_factory.cc",
        "table/block_based_table_reader.cc",
        "table/block_builder.cc",
        "table/block_fetcher.cc",
        "table/block_prefix_index.cc",
        "table/bloom_block.cc",
        "table/cuckoo_table_builder.cc",
        "table/cuckoo_table_factory.cc",
        "table/cuckoo_table_reader.cc",
        "table/flush_block_policy.cc",
        "table/format.cc",
        "table/full_filter_block.cc",
        "table/get_context.cc",
        "table/index_builder.cc",
        "table/iterator.cc",
        "table/merging_iterator.cc",
        "table/meta_blocks.cc",
        "table/partitioned_filter_block.cc",
        "table/persistent_cache_helper.cc",
        "table/plain_table_builder.cc",
        "table/plain_table_factory.cc",
        "table/plain_table_index.cc",
        "table/plain_table_key_coding.cc",
        "table/plain_table_reader.cc",
        "table/sst_file_writer.cc",
        "table/table_properties.cc",
        "table/two_level_iterator.cc",
        "tools/dump/db_dump_tool.cc",
        "tools/ldb_cmd.cc",
        "tools/ldb_tool.cc",
        "tools/sst_dump_tool.cc",
        "util/arena.cc",
        "util/auto_roll_logger.cc",
        "util/bloom.cc",
        "util/build_version.cc",
        "util/coding.cc",
        "util/compaction_job_stats_impl.cc",
        "util/comparator.cc",
        "util/concurrent_arena.cc",
        "util/crc32c.cc",
        "util/delete_scheduler.cc",
        "util/dynamic_bloom.cc",
        "util/event_logger.cc",
        "util/file_reader_writer.cc",
        "util/file_util.cc",
        "util/filename.cc",
        "util/filter_policy.cc",
        "util/hash.cc",
        "util/log_buffer.cc",
        "util/murmurhash.cc",
        "util/random.cc",
        "util/rate_limiter.cc",
        "util/slice.cc",
        "util/sst_file_manager_impl.cc",
        "util/status.cc",
        "util/status_message.cc",
        "util/string_util.cc",
        "util/sync_point.cc",
        "util/thread_local.cc",
        "util/threadpool_imp.cc",
        "util/transaction_test_util.cc",
        "util/xxhash.cc",
        "utilities/backupable/backupable_db.cc",
        "utilities/blob_db/blob_db.cc",
        "utilities/blob_db/blob_db_impl.cc",
        "utilities/blob_db/blob_dump_tool.cc",
        "utilities/blob_db/blob_file.cc",
        "utilities/blob_db/blob_log_format.cc",
        "utilities/blob_db/blob_log_reader.cc",
        "utilities/blob_db/blob_log_writer.cc",
        "utilities/blob_db/ttl_extractor.cc",
        "utilities/cassandra/cassandra_compaction_filter.cc",
        "utilities/cassandra/format.cc",
        "utilities/cassandra/merge_operator.cc",
        "utilities/checkpoint/checkpoint_impl.cc",
        "utilities/compaction_filters/remove_emptyvalue_compactionfilter.cc",
        "utilities/convenience/info_log_finder.cc",
        "utilities/date_tiered/date_tiered_db_impl.cc",
        "utilities/debug.cc",
        "utilities/document/document_db.cc",
        "utilities/document/json_document.cc",
        "utilities/document/json_document_builder.cc",
        "utilities/env_mirror.cc",
        "utilities/env_timed.cc",
        "utilities/geodb/geodb_impl.cc",
        "utilities/leveldb_options/leveldb_options.cc",
        "utilities/lua/rocks_lua_compaction_filter.cc",
        "utilities/memory/memory_util.cc",
        "utilities/merge_operators/max.cc",
        "utilities/merge_operators/put.cc",
        "utilities/merge_operators/string_append/stringappend.cc",
        "utilities/merge_operators/string_append/stringappend2.cc",
        "utilities/merge_operators/uint64add.cc",
        "utilities/option_change_migration/option_change_migration.cc",
        "utilities/options/options_util.cc",
        "utilities/persistent_cache/block_cache_tier.cc",
        "utilities/persistent_cache/block_cache_tier_file.cc",
        "utilities/persistent_cache/block_cache_tier_metadata.cc",
        "utilities/persistent_cache/persistent_cache_tier.cc",
        "utilities/persistent_cache/volatile_tier_impl.cc",
        "utilities/redis/redis_lists.cc",
        "utilities/simulator_cache/sim_cache.cc",
        "utilities/spatialdb/spatial_db.cc",
        "utilities/table_properties_collectors/compact_on_deletion_collector.cc",
        "utilities/transactions/optimistic_transaction.cc",
        "utilities/transactions/optimistic_transaction_db_impl.cc",
        "utilities/transactions/pessimistic_transaction.cc",
        "utilities/transactions/pessimistic_transaction_db.cc",
        "utilities/transactions/snapshot_checker.cc",
        "utilities/transactions/transaction_base.cc",
        "utilities/transactions/transaction_db_mutex_impl.cc",
        "utilities/transactions/transaction_lock_mgr.cc",
        "utilities/transactions/transaction_util.cc",
        "utilities/transactions/write_prepared_txn.cc",
        "utilities/transactions/write_prepared_txn_db.cc",
        "utilities/ttl/db_ttl_impl.cc",
        "utilities/write_batch_with_index/write_batch_with_index.cc",
        "utilities/write_batch_with_index/write_batch_with_index_internal.cc",
    ],
    headers = ['third-party/gtest-1.7.0/fused-src/gtest/gtest.h', 'third-party/fbson/FbsonStream.h', 'third-party/fbson/FbsonDocument.h', 'third-party/fbson/FbsonWriter.h', 'third-party/fbson/FbsonJsonParser.h', 'third-party/fbson/FbsonUtil.h', 'util/cast_util.h', 'util/hash.h', 'util/thread_operation.h', 'util/channel.h', 'util/concurrent_arena.h', 'util/mutexlock.h', 'util/build_version.h', 'util/memory_usage.h', 'util/threadpool_imp.h', 'util/file_reader_writer.h', 'util/aligned_buffer.h', 'util/stderr_logger.h', 'util/mpsc.h', 'util/compression.h', 'util/timer_queue.h', 'util/random.h', 'util/allocator.h', 'util/testharness.h', 'util/filename.h', 'util/arena.h', 'util/string_util.h', 'util/kv_map.h', 'util/core_local.h', 'util/hash_map.h', 'util/coding.h', 'util/heap.h', 'util/logging.h', 'util/xxhash.h', 'util/auto_roll_logger.h', 'util/testutil.h', 'util/sync_point.h', 'util/dynamic_bloom.h', 'util/murmurhash.h', 'util/delete_scheduler.h', 'util/crc32c.h', 'util/crc32c_ppc.h', 'util/file_util.h', 'util/rate_limiter.h', 'util/ppc-opcode.h', 'util/event_logger.h', 'util/fault_injection_test_env.h', 'util/crc32c_ppc_constants.h', 'util/sst_file_manager_impl.h', 'util/thread_local.h', 'util/gflags_compat.h', 'util/stop_watch.h', 'util/log_buffer.h', 'util/transaction_test_util.h', 'util/autovector.h', 'port/likely.h', 'port/sys_time.h', 'port/dirent.h', 'port/stack_trace.h', 'port/util_logger.h', 'port/xpress.h', 'port/port.h', 'port/port_posix.h', 'port/port_example.h', 'port/win/win_thread.h', 'port/win/xpress_win.h', 'port/win/port_win.h', 'port/win/win_logger.h', 'port/win/io_win.h', 'port/win/env_win.h', 'cache/clock_cache.h', 'cache/lru_cache.h', 'cache/sharded_cache.h', 'tools/sst_dump_tool_imp.h', 'tools/ldb_cmd_impl.h', 'tools/rdb/db_wrapper.h', 'db/version_set.h', 'db/compacted_db_impl.h', 'db/log_writer.h', 'db/compaction_picker.h', 'db/snapshot_impl.h', 'db/range_del_aggregator.h', 'db/table_properties_collector.h', 'db/log_reader.h', 'db/compaction_job.h', 'db/managed_iterator.h', 'db/db_impl.h', 'db/compaction_iterator.h', 'db/db_impl_readonly.h', 'db/memtable_list.h', 'db/log_format.h', 'db/wal_manager.h', 'db/event_helpers.h', 'db/memtable.h', 'db/write_callback.h', 'db/snapshot_checker.h', 'db/pre_release_callback.h', 'db/write_thread.h', 'db/write_batch_internal.h', 'db/db_info_dumper.h', 'db/malloc_stats.h', 'db/dbformat.h', 'db/file_indexer.h', 'db/internal_stats.h', 'db/compaction.h', 'db/table_cache.h', 'db/flush_job.h', 'db/builder.h', 'db/merge_context.h', 'db/compaction_picker_universal.h', 'db/db_test_util.h', 'db/transaction_log_impl.h', 'db/compaction_iteration_stats.h', 'db/job_context.h', 'db/read_callback.h', 'db/column_family.h', 'db/forward_iterator.h', 'db/version_edit.h', 'db/version_builder.h', 'db/merge_helper.h', 'db/db_iter.h', 'db/write_controller.h', 'db/external_sst_file_ingestion_job.h', 'db/pinned_iterators_manager.h', 'db/flush_scheduler.h', 'include/rocksdb/filter_policy.h', 'include/rocksdb/slice_transform.h', 'include/rocksdb/sst_file_writer.h', 'include/rocksdb/merge_operator.h', 'include/rocksdb/cleanable.h', 'include/rocksdb/flush_block_policy.h', 'include/rocksdb/iostats_context.h', 'include/rocksdb/write_batch_base.h', 'include/rocksdb/write_batch.h', 'include/rocksdb/slice.h', 'include/rocksdb/env_encryption.h', 'include/rocksdb/cache.h', 'include/rocksdb/db_dump_tool.h', 'include/rocksdb/universal_compaction.h', 'include/rocksdb/db_bench_tool.h', 'include/rocksdb/perf_context.h', 'include/rocksdb/sst_dump_tool.h', 'include/rocksdb/types.h', 'include/rocksdb/table.h', 'include/rocksdb/iterator.h', 'include/rocksdb/write_buffer_manager.h', 'include/rocksdb/memtablerep.h', 'include/rocksdb/version.h', 'include/rocksdb/c.h', 'include/rocksdb/advanced_options.h', 'include/rocksdb/statistics.h', 'include/rocksdb/snapshot.h', 'include/rocksdb/compaction_job_stats.h', 'include/rocksdb/compaction_filter.h', 'include/rocksdb/status.h', 'include/rocksdb/threadpool.h', 'include/rocksdb/ldb_tool.h', 'include/rocksdb/db.h', 'include/rocksdb/table_properties.h', 'include/rocksdb/perf_level.h', 'include/rocksdb/rate_limiter.h', 'include/rocksdb/wal_filter.h', 'include/rocksdb/options.h', 'include/rocksdb/transaction_log.h', 'include/rocksdb/experimental.h', 'include/rocksdb/listener.h', 'include/rocksdb/sst_file_manager.h', 'include/rocksdb/persistent_cache.h', 'include/rocksdb/env.h', 'include/rocksdb/convenience.h', 'include/rocksdb/comparator.h', 'include/rocksdb/thread_status.h', 'include/rocksdb/metadata.h', 'include/rocksdb/utilities/write_batch_with_index.h', 'include/rocksdb/utilities/table_properties_collectors.h', 'include/rocksdb/utilities/json_document.h', 'include/rocksdb/utilities/option_change_migration.h', 'include/rocksdb/utilities/env_librados.h', 'include/rocksdb/utilities/transaction_db.h', 'include/rocksdb/utilities/ldb_cmd.h', 'include/rocksdb/utilities/options_util.h', 'include/rocksdb/utilities/debug.h', 'include/rocksdb/utilities/document_db.h', 'include/rocksdb/utilities/db_ttl.h', 'include/rocksdb/utilities/backupable_db.h', 'include/rocksdb/utilities/checkpoint.h', 'include/rocksdb/utilities/transaction_db_mutex.h', 'include/rocksdb/utilities/sim_cache.h', 'include/rocksdb/utilities/info_log_finder.h', 'include/rocksdb/utilities/leveldb_options.h', 'include/rocksdb/utilities/env_mirror.h', 'include/rocksdb/utilities/ldb_cmd_execute_result.h', 'include/rocksdb/utilities/utility_db.h', 'include/rocksdb/utilities/object_registry.h', 'include/rocksdb/utilities/date_tiered_db.h', 'include/rocksdb/utilities/spatial_db.h', 'include/rocksdb/utilities/stackable_db.h', 'include/rocksdb/utilities/transaction.h', 'include/rocksdb/utilities/memory_util.h', 'include/rocksdb/utilities/geo_db.h', 'include/rocksdb/utilities/convenience.h', 'include/rocksdb/utilities/optimistic_transaction_db.h', 'include/rocksdb/utilities/lua/rocks_lua_custom_library.h', 'include/rocksdb/utilities/lua/rocks_lua_util.h', 'include/rocksdb/utilities/lua/rocks_lua_compaction_filter.h', 'monitoring/perf_step_timer.h', 'monitoring/instrumented_mutex.h', 'monitoring/perf_level_imp.h', 'monitoring/iostats_context_imp.h', 'monitoring/histogram_windowing.h', 'monitoring/statistics.h', 'monitoring/thread_status_updater.h', 'monitoring/thread_status_util.h', 'monitoring/file_read_sample.h', 'monitoring/histogram.h', 'monitoring/perf_context_imp.h', 'memtable/hash_skiplist_rep.h', 'memtable/stl_wrappers.h', 'memtable/hash_cuckoo_rep.h', 'memtable/skiplist.h', 'memtable/hash_linklist_rep.h', 'memtable/inlineskiplist.h', 'utilities/merge_operators.h', 'utilities/column_aware_encoding_util.h', 'utilities/col_buf_decoder.h', 'utilities/col_buf_encoder.h', 'utilities/transactions/pessimistic_transaction.h', 'utilities/transactions/transaction_lock_mgr.h', 'utilities/transactions/transaction_test.h', 'utilities/transactions/transaction_base.h', 'utilities/transactions/transaction_db_mutex_impl.h', 'utilities/transactions/optimistic_transaction_db_impl.h', 'utilities/transactions/write_prepared_txn_db.h', 'utilities/transactions/transaction_util.h', 'utilities/transactions/write_prepared_txn.h', 'utilities/transactions/pessimistic_transaction_db.h', 'utilities/transactions/optimistic_transaction.h', 'utilities/blob_db/blob_compaction_filter.h', 'utilities/blob_db/blob_log_format.h', 'utilities/blob_db/blob_log_writer.h', 'utilities/blob_db/blob_db_iterator.h', 'utilities/blob_db/blob_dump_tool.h', 'utilities/blob_db/blob_index.h', 'utilities/blob_db/blob_db_impl.h', 'utilities/blob_db/blob_db.h', 'utilities/blob_db/blob_file.h', 'utilities/blob_db/blob_log_reader.h', 'utilities/geodb/geodb_impl.h', 'utilities/compaction_filters/remove_emptyvalue_compactionfilter.h', 'utilities/spatialdb/utils.h', 'utilities/redis/redis_list_exception.h', 'utilities/redis/redis_list_iterator.h', 'utilities/redis/redis_lists.h', 'utilities/write_batch_with_index/write_batch_with_index_internal.h', 'utilities/persistent_cache/block_cache_tier.h', 'utilities/persistent_cache/persistent_cache_tier.h', 'utilities/persistent_cache/block_cache_tier_file_buffer.h', 'utilities/persistent_cache/persistent_cache_test.h', 'utilities/persistent_cache/block_cache_tier_metadata.h', 'utilities/persistent_cache/lrulist.h', 'utilities/persistent_cache/hash_table.h', 'utilities/persistent_cache/volatile_tier_impl.h', 'utilities/persistent_cache/block_cache_tier_file.h', 'utilities/persistent_cache/hash_table_evictable.h', 'utilities/persistent_cache/persistent_cache_util.h', 'utilities/table_properties_collectors/compact_on_deletion_collector.h', 'utilities/ttl/db_ttl_impl.h', 'utilities/date_tiered/date_tiered_db_impl.h', 'utilities/cassandra/merge_operator.h', 'utilities/cassandra/test_utils.h', 'utilities/cassandra/cassandra_compaction_filter.h', 'utilities/cassandra/serialize.h', 'utilities/cassandra/format.h', 'utilities/checkpoint/checkpoint_impl.h', 'utilities/merge_operators/string_append/stringappend2.h', 'utilities/merge_operators/string_append/stringappend.h', 'table/plain_table_reader.h', 'table/block_builder.h', 'table/filter_block.h', 'table/plain_table_builder.h', 'table/two_level_iterator.h', 'table/block_fetcher.h', 'table/sst_file_writer_collectors.h', 'table/adaptive_table_factory.h', 'table/merging_iterator.h', 'table/full_filter_block.h', 'table/plain_table_key_coding.h', 'table/bloom_block.h', 'table/persistent_cache_helper.h', 'table/cuckoo_table_factory.h', 'table/iterator_wrapper.h', 'table/scoped_arena_iterator.h', 'table/block_based_filter_block.h', 'table/block_prefix_index.h', 'table/meta_blocks.h', 'table/block.h', 'table/index_builder.h', 'table/plain_table_index.h', 'table/cuckoo_table_builder.h', 'table/partitioned_filter_block.h', 'table/block_based_table_builder.h', 'table/internal_iterator.h', 'table/table_reader.h', 'table/full_filter_bits_builder.h', 'table/table_builder.h', 'table/block_based_table_factory.h', 'table/plain_table_factory.h', 'table/mock_table.h', 'table/table_properties_internal.h', 'table/persistent_cache_options.h', 'table/get_context.h', 'table/cuckoo_table_reader.h', 'table/block_based_table_reader.h', 'table/iter_heap.h', 'table/format.h', 'options/options_helper.h', 'options/db_options.h', 'options/cf_options.h', 'options/options_sanity_check.h', 'options/options_parser.h', 'env/mock_env.h', 'env/posix_logger.h', 'env/io_posix.h', 'env/env_chroot.h', 'hdfs/env_hdfs.h'],
    compiler_flags = rocksdb_compiler_flags,
    preprocessor_flags = rocksdb_preprocessor_flags,
    deps = [],
    #external_deps = rocksdb_external_deps,
)

cxx_library(
    name = "rocksdb_test_lib",
    srcs = [
        "db/db_test_util.cc",
        "table/mock_table.cc",
        "util/fault_injection_test_env.cc",
        "util/testharness.cc",
        "util/testutil.cc",
        "utilities/cassandra/test_utils.cc",
        "utilities/col_buf_decoder.cc",
        "utilities/col_buf_encoder.cc",
        "utilities/column_aware_encoding_util.cc",
    ],
    headers = [],
    compiler_flags = rocksdb_compiler_flags,
    preprocessor_flags = rocksdb_preprocessor_flags,
    deps = [":rocksdb_lib"],
    #external_deps = rocksdb_external_deps,
)

cxx_library(
    name = "rocksdb_tools_lib",
    srcs = [
        "tools/db_bench_tool.cc",
        "util/testutil.cc",
    ],
    headers = [],
    compiler_flags = rocksdb_compiler_flags,
    preprocessor_flags = rocksdb_preprocessor_flags,
    deps = [":rocksdb_lib"],
    #external_deps = rocksdb_external_deps,
)

cxx_library(
    name = "env_basic_test_lib",
    srcs = ["env/env_basic_test.cc"],
    headers = [],
    compiler_flags = rocksdb_compiler_flags,
    preprocessor_flags = rocksdb_preprocessor_flags,
    deps = [":rocksdb_test_lib"],
    #external_deps = rocksdb_external_deps,
)

# [test_name, test_src, test_type]
ROCKS_TESTS = [
    [
        "arena_test",
        "util/arena_test.cc",
        "serial",
    ],
    [
        "auto_roll_logger_test",
        "util/auto_roll_logger_test.cc",
        "serial",
    ],
    [
        "autovector_test",
        "util/autovector_test.cc",
        "serial",
    ],
    [
        "backupable_db_test",
        "utilities/backupable/backupable_db_test.cc",
        "parallel",
    ],
    [
        "blob_db_test",
        "utilities/blob_db/blob_db_test.cc",
        "serial",
    ],
    [
        "block_based_filter_block_test",
        "table/block_based_filter_block_test.cc",
        "serial",
    ],
    [
        "block_test",
        "table/block_test.cc",
        "serial",
    ],
    [
        "bloom_test",
        "util/bloom_test.cc",
        "serial",
    ],
    [
        "c_test",
        "db/c_test.c",
        "serial",
    ],
    [
        "cache_test",
        "cache/cache_test.cc",
        "serial",
    ],
    [
        "cassandra_format_test",
        "utilities/cassandra/cassandra_format_test.cc",
        "serial",
    ],
    [
        "cassandra_functional_test",
        "utilities/cassandra/cassandra_functional_test.cc",
        "serial",
    ],
    [
        "cassandra_row_merge_test",
        "utilities/cassandra/cassandra_row_merge_test.cc",
        "serial",
    ],
    [
        "cassandra_serialize_test",
        "utilities/cassandra/cassandra_serialize_test.cc",
        "serial",
    ],
    [
        "checkpoint_test",
        "utilities/checkpoint/checkpoint_test.cc",
        "serial",
    ],
    [
        "cleanable_test",
        "table/cleanable_test.cc",
        "serial",
    ],
    [
        "coding_test",
        "util/coding_test.cc",
        "serial",
    ],
    [
        "column_aware_encoding_test",
        "utilities/column_aware_encoding_test.cc",
        "serial",
    ],
    [
        "column_family_test",
        "db/column_family_test.cc",
        "serial",
    ],
    [
        "compact_files_test",
        "db/compact_files_test.cc",
        "serial",
    ],
    [
        "compact_on_deletion_collector_test",
        "utilities/table_properties_collectors/compact_on_deletion_collector_test.cc",
        "serial",
    ],
    [
        "compaction_iterator_test",
        "db/compaction_iterator_test.cc",
        "serial",
    ],
    [
        "compaction_job_stats_test",
        "db/compaction_job_stats_test.cc",
        "serial",
    ],
    [
        "compaction_job_test",
        "db/compaction_job_test.cc",
        "serial",
    ],
    [
        "compaction_picker_test",
        "db/compaction_picker_test.cc",
        "serial",
    ],
    [
        "comparator_db_test",
        "db/comparator_db_test.cc",
        "serial",
    ],
    [
        "corruption_test",
        "db/corruption_test.cc",
        "serial",
    ],
    [
        "crc32c_test",
        "util/crc32c_test.cc",
        "serial",
    ],
    [
        "cuckoo_table_builder_test",
        "table/cuckoo_table_builder_test.cc",
        "serial",
    ],
    [
        "cuckoo_table_db_test",
        "db/cuckoo_table_db_test.cc",
        "serial",
    ],
    [
        "cuckoo_table_reader_test",
        "table/cuckoo_table_reader_test.cc",
        "serial",
    ],
    [
        "date_tiered_test",
        "utilities/date_tiered/date_tiered_test.cc",
        "serial",
    ],
    [
        "db_basic_test",
        "db/db_basic_test.cc",
        "serial",
    ],
    [
        "db_blob_index_test",
        "db/db_blob_index_test.cc",
        "serial",
    ],
    [
        "db_block_cache_test",
        "db/db_block_cache_test.cc",
        "serial",
    ],
    [
        "db_bloom_filter_test",
        "db/db_bloom_filter_test.cc",
        "serial",
    ],
    [
        "db_compaction_filter_test",
        "db/db_compaction_filter_test.cc",
        "parallel",
    ],
    [
        "db_compaction_test",
        "db/db_compaction_test.cc",
        "parallel",
    ],
    [
        "db_dynamic_level_test",
        "db/db_dynamic_level_test.cc",
        "serial",
    ],
    [
        "db_encryption_test",
        "db/db_encryption_test.cc",
        "serial",
    ],
    [
        "db_flush_test",
        "db/db_flush_test.cc",
        "serial",
    ],
    [
        "db_inplace_update_test",
        "db/db_inplace_update_test.cc",
        "serial",
    ],
    [
        "db_io_failure_test",
        "db/db_io_failure_test.cc",
        "serial",
    ],
    [
        "db_iter_test",
        "db/db_iter_test.cc",
        "serial",
    ],
    [
        "db_iterator_test",
        "db/db_iterator_test.cc",
        "serial",
    ],
    [
        "db_log_iter_test",
        "db/db_log_iter_test.cc",
        "serial",
    ],
    [
        "db_memtable_test",
        "db/db_memtable_test.cc",
        "serial",
    ],
    [
        "db_merge_operator_test",
        "db/db_merge_operator_test.cc",
        "parallel",
    ],
    [
        "db_options_test",
        "db/db_options_test.cc",
        "serial",
    ],
    [
        "db_properties_test",
        "db/db_properties_test.cc",
        "serial",
    ],
    [
        "db_range_del_test",
        "db/db_range_del_test.cc",
        "serial",
    ],
    [
        "db_sst_test",
        "db/db_sst_test.cc",
        "parallel",
    ],
    [
        "db_statistics_test",
        "db/db_statistics_test.cc",
        "serial",
    ],
    [
        "db_table_properties_test",
        "db/db_table_properties_test.cc",
        "serial",
    ],
    [
        "db_tailing_iter_test",
        "db/db_tailing_iter_test.cc",
        "serial",
    ],
    [
        "db_test",
        "db/db_test.cc",
        "parallel",
    ],
    [
        "db_test2",
        "db/db_test2.cc",
        "serial",
    ],
    [
        "db_universal_compaction_test",
        "db/db_universal_compaction_test.cc",
        "parallel",
    ],
    [
        "db_wal_test",
        "db/db_wal_test.cc",
        "parallel",
    ],
    [
        "db_write_test",
        "db/db_write_test.cc",
        "serial",
    ],
    [
        "dbformat_test",
        "db/dbformat_test.cc",
        "serial",
    ],
    [
        "delete_scheduler_test",
        "util/delete_scheduler_test.cc",
        "serial",
    ],
    [
        "deletefile_test",
        "db/deletefile_test.cc",
        "serial",
    ],
    [
        "document_db_test",
        "utilities/document/document_db_test.cc",
        "serial",
    ],
    [
        "dynamic_bloom_test",
        "util/dynamic_bloom_test.cc",
        "serial",
    ],
    [
        "env_basic_test",
        "env/env_basic_test.cc",
        "serial",
    ],
    [
        "env_test",
        "env/env_test.cc",
        "serial",
    ],
    [
        "env_timed_test",
        "utilities/env_timed_test.cc",
        "serial",
    ],
    [
        "event_logger_test",
        "util/event_logger_test.cc",
        "serial",
    ],
    [
        "external_sst_file_basic_test",
        "db/external_sst_file_basic_test.cc",
        "serial",
    ],
    [
        "external_sst_file_test",
        "db/external_sst_file_test.cc",
        "parallel",
    ],
    [
        "fault_injection_test",
        "db/fault_injection_test.cc",
        "parallel",
    ],
    [
        "file_indexer_test",
        "db/file_indexer_test.cc",
        "serial",
    ],
    [
        "file_reader_writer_test",
        "util/file_reader_writer_test.cc",
        "serial",
    ],
    [
        "filelock_test",
        "util/filelock_test.cc",
        "serial",
    ],
    [
        "filename_test",
        "db/filename_test.cc",
        "serial",
    ],
    [
        "flush_job_test",
        "db/flush_job_test.cc",
        "serial",
    ],
    [
        "full_filter_block_test",
        "table/full_filter_block_test.cc",
        "serial",
    ],
    [
        "geodb_test",
        "utilities/geodb/geodb_test.cc",
        "serial",
    ],
    [
        "hash_table_test",
        "utilities/persistent_cache/hash_table_test.cc",
        "serial",
    ],
    [
        "hash_test",
        "util/hash_test.cc",
        "serial",
    ],
    [
        "heap_test",
        "util/heap_test.cc",
        "serial",
    ],
    [
        "histogram_test",
        "monitoring/histogram_test.cc",
        "serial",
    ],
    [
        "inlineskiplist_test",
        "memtable/inlineskiplist_test.cc",
        "parallel",
    ],
    [
        "iostats_context_test",
        "monitoring/iostats_context_test.cc",
        "serial",
    ],
    [
        "json_document_test",
        "utilities/document/json_document_test.cc",
        "serial",
    ],
    [
        "ldb_cmd_test",
        "tools/ldb_cmd_test.cc",
        "serial",
    ],
    [
        "listener_test",
        "db/listener_test.cc",
        "serial",
    ],
    [
        "log_test",
        "db/log_test.cc",
        "serial",
    ],
    [
        "lru_cache_test",
        "cache/lru_cache_test.cc",
        "serial",
    ],
    [
        "manual_compaction_test",
        "db/manual_compaction_test.cc",
        "parallel",
    ],
    [
        "memory_test",
        "utilities/memory/memory_test.cc",
        "serial",
    ],
    [
        "memtable_list_test",
        "db/memtable_list_test.cc",
        "serial",
    ],
    [
        "merge_helper_test",
        "db/merge_helper_test.cc",
        "serial",
    ],
    [
        "merge_test",
        "db/merge_test.cc",
        "serial",
    ],
    [
        "merger_test",
        "table/merger_test.cc",
        "serial",
    ],
    [
        "mock_env_test",
        "env/mock_env_test.cc",
        "serial",
    ],
    [
        "object_registry_test",
        "utilities/object_registry_test.cc",
        "serial",
    ],
    [
        "optimistic_transaction_test",
        "utilities/transactions/optimistic_transaction_test.cc",
        "serial",
    ],
    [
        "option_change_migration_test",
        "utilities/option_change_migration/option_change_migration_test.cc",
        "serial",
    ],
    [
        "options_file_test",
        "db/options_file_test.cc",
        "serial",
    ],
    [
        "options_settable_test",
        "options/options_settable_test.cc",
        "serial",
    ],
    [
        "options_test",
        "options/options_test.cc",
        "serial",
    ],
    [
        "options_util_test",
        "utilities/options/options_util_test.cc",
        "serial",
    ],
    [
        "partitioned_filter_block_test",
        "table/partitioned_filter_block_test.cc",
        "serial",
    ],
    [
        "perf_context_test",
        "db/perf_context_test.cc",
        "serial",
    ],
    [
        "persistent_cache_test",
        "utilities/persistent_cache/persistent_cache_test.cc",
        "parallel",
    ],
    [
        "plain_table_db_test",
        "db/plain_table_db_test.cc",
        "serial",
    ],
    [
        "prefix_test",
        "db/prefix_test.cc",
        "serial",
    ],
    [
        "range_del_aggregator_test",
        "db/range_del_aggregator_test.cc",
        "serial",
    ],
    [
        "rate_limiter_test",
        "util/rate_limiter_test.cc",
        "serial",
    ],
    [
        "reduce_levels_test",
        "tools/reduce_levels_test.cc",
        "serial",
    ],
    [
        "repair_test",
        "db/repair_test.cc",
        "serial",
    ],
    [
        "sim_cache_test",
        "utilities/simulator_cache/sim_cache_test.cc",
        "serial",
    ],
    [
        "skiplist_test",
        "memtable/skiplist_test.cc",
        "serial",
    ],
    [
        "slice_transform_test",
        "util/slice_transform_test.cc",
        "serial",
    ],
    [
        "spatial_db_test",
        "utilities/spatialdb/spatial_db_test.cc",
        "serial",
    ],
    [
        "sst_dump_test",
        "tools/sst_dump_test.cc",
        "serial",
    ],
    [
        "statistics_test",
        "monitoring/statistics_test.cc",
        "serial",
    ],
    [
        "stringappend_test",
        "utilities/merge_operators/string_append/stringappend_test.cc",
        "serial",
    ],
    [
        "table_properties_collector_test",
        "db/table_properties_collector_test.cc",
        "serial",
    ],
    [
        "table_test",
        "table/table_test.cc",
        "parallel",
    ],
    [
        "thread_list_test",
        "util/thread_list_test.cc",
        "serial",
    ],
    [
        "thread_local_test",
        "util/thread_local_test.cc",
        "serial",
    ],
    [
        "timer_queue_test",
        "util/timer_queue_test.cc",
        "serial",
    ],
    [
        "transaction_test",
        "utilities/transactions/transaction_test.cc",
        "parallel",
    ],
    [
        "ttl_test",
        "utilities/ttl/ttl_test.cc",
        "serial",
    ],
    [
        "util_merge_operators_test",
        "utilities/util_merge_operators_test.cc",
        "serial",
    ],
    [
        "version_builder_test",
        "db/version_builder_test.cc",
        "serial",
    ],
    [
        "version_edit_test",
        "db/version_edit_test.cc",
        "serial",
    ],
    [
        "version_set_test",
        "db/version_set_test.cc",
        "serial",
    ],
    [
        "wal_manager_test",
        "db/wal_manager_test.cc",
        "serial",
    ],
    [
        "write_batch_test",
        "db/write_batch_test.cc",
        "serial",
    ],
    [
        "write_batch_with_index_test",
        "utilities/write_batch_with_index/write_batch_with_index_test.cc",
        "serial",
    ],
    [
        "write_buffer_manager_test",
        "memtable/write_buffer_manager_test.cc",
        "serial",
    ],
    [
        "write_callback_test",
        "db/write_callback_test.cc",
        "serial",
    ],
    [
        "write_controller_test",
        "db/write_controller_test.cc",
        "serial",
    ],
    [
        "write_prepared_transaction_test",
        "utilities/transactions/write_prepared_transaction_test.cc",
        "parallel",
    ],
]

# Generate a test rule for each entry in ROCKS_TESTS
# Do not build the tests in opt mode, since SyncPoint and other test code
# will not be included.
#if not is_opt_mode:
for test_cfg in ROCKS_TESTS:
    test_name = test_cfg[0]
    test_cc = test_cfg[1]
    ttype = "gtest" if test_cfg[2] == "parallel" else "simple"
    test_bin = test_name + "_bin"

    cxx_binary (
      name = test_bin,
      srcs = [test_cc],
      deps = [":rocksdb_test_lib"],
      preprocessor_flags = rocksdb_preprocessor_flags,
      compiler_flags = rocksdb_compiler_flags,
      #external_deps = rocksdb_external_deps,
    )
