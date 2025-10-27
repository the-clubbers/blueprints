# 🔁 Task-Cycle: done → set due date → auto re-enable

This blueprint manages recurring tasks in Home Assistant using an `input_boolean` and an `input_datetime`.

When the task is marked as "done" (input_boolean turned OFF), the automation sets a new due date.  
Every day (or when manually triggered), it checks whether the task is due and re-enables it if necessary.

---

## ✅ Features

- Automatically sets a new due date when a task is marked as done
- Checks daily if the task is due again
- Reactivates the task automatically on the due date
- Works with any task that repeats on a time-based cycle

---

## 🛠 Requirements

You need one `input_boolean` and one `input_datetime` per task:

- `input_boolean`: toggle for the task (ON = active, OFF = done)
- `input_datetime`: date field to store the next due date (date only, no time)

---

## ⚙️ Example Helper Configuration (YAML)

You can define helpers manually in your YAML config or via the UI (Settings → Devices & Services → Helpers).

```yaml
# input_boolean for the task
input_boolean:
  task_filter_clean:
    name: "Task: Clean filter"
    icon: mdi:air-filter

# input_datetime for the due date
input_datetime:
  due_filter_clean:
    name: "Due date: Clean filter"
    has_date: true
    has_time: false
```

---

## 🧩 Example Blueprint Inputs

After importing the blueprint, create a new automation using it with these inputs:

| Field                     | Value                                 |
|--------------------------|---------------------------------------|
| Task toggle              | `input_boolean.task_filter_clean`     |
| Due date                 | `input_datetime.due_filter_clean`     |
| Days until next due date | `120`                                 |
| Daily check time         | `03:00:00`                            |

---

## 🧪 Example Workflow

1. Task is ON → visible as a reminder in UI
2. You turn the toggle OFF (task done)
3. Due date is set to today + 120 days
4. Daily at 3:00 AM → if due date is today or earlier and task is still OFF → task is re-enabled

---

## 📥 Import the Blueprint

Paste this URL directly into Home Assistant to import the blueprint:

```
https://raw.githubusercontent.com/the-clubbers/blueprints/refs/heads/main/task-cycle.yaml
```

Paste it into Home Assistant under:  
**Settings → Automations & Scenes → Blueprints → Import Blueprint**

---

## 🧼 License

MIT – feel free to copy, adapt and share.
