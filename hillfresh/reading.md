bench --site test.hillfresh.co.ke migrate --skip-failing --skip-search-index
Migrating test.hillfresh.co.ke
Killed inactive database connection with PID 754
Updating DocTypes for frappe        : [========================================] 100%
Updating DocTypes for erpnext       : [========================================] 100%
Updating DocTypes for hrms          : [========================================] 100%
Updating DocTypes for icrm          : [========================================] 100%
Syncing jobs...
Syncing fixtures...

Traceback (most recent call last):
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/utils/bench_helper.py", line 48, in invoke
    return super().invoke(ctx)
           ^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/env/lib/python3.12/site-packages/click/core.py", line 1697, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/env/lib/python3.12/site-packages/click/core.py", line 1443, in invoke
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/env/lib/python3.12/site-packages/click/core.py", line 788, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/env/lib/python3.12/site-packages/click/decorators.py", line 33, in new_func
    return f(get_current_context(), *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/commands/__init__.py", line 28, in _func
    ret = f(ctx.obj, *args, **kwargs)
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/commands/site.py", line 701, in migrate
    ).run(site=site)
      ^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/migrate.py", line 249, in run
    self.post_schema_updates()
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/migrate.py", line 53, in wrapper
    raise e
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/migrate.py", line 45, in wrapper
    ret = method(*args, **kwargs)
          ^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/migrate.py", line 147, in post_schema_updates
    sync_fixtures()
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/utils/fixtures.py", line 22, in sync_fixtures
    import_fixtures(app)
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/utils/fixtures.py", line 41, in import_fixtures
    import_doc(file_path, sort=True)
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/core/doctype/data_import/data_import.py", line 279, in import_doc
    import_file_by_path(
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/modules/import_file.py", line 142, in import_file_by_path
    import_doc(
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/modules/import_file.py", line 235, in import_doc
    doc.insert()
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 123, in wrapper
    return func(self, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 412, in insert
    self.run_before_save_methods()
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 1280, in run_before_save_methods
    self.run_method("validate")
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 1128, in run_method
    out = Document.hook(fn)(self, *args, **kwargs)
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 1516, in composer
    return composed(self, method, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 1494, in runner
    add_to_return_value(self, fn(self, *args, **kwargs))
                              ^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 1125, in fn
    return method_object(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/core/doctype/doctype/doctype.py", line 210, in validate
    self.make_repeatable()
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/core/doctype/doctype/doctype.py", line 923, in make_repeatable
    create_custom_field(self.name, df, ignore_validate=True)
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/custom/doctype/custom_field/custom_field.py", line 310, in create_custom_field
    custom_field.insert()
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 123, in wrapper
    return func(self, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 404, in insert
    self._validate_links()
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/model/document.py", line 1096, in _validate_links
    frappe.throw(_("Could not find {0}").format(msg), frappe.LinkValidationError)
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/utils/messages.py", line 145, in throw
    msgprint(
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/utils/messages.py", line 106, in msgprint
    _raise_exception()
  File "/home/hillfresh/frappe-bench/apps/frappe/frappe/utils/messages.py", line 57, in _raise_exception
    raise exc
frappe.exceptions.LinkValidationError: Could not find DocType: Payment Entry

Could not find DocType: Payment Entry