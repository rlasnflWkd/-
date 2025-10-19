# -import tkinter as tk
from datetime import datetime, timedelta

# 공부 기록 저장용
study_start = None
total_study_time = timedelta(0)

def start_study():
    global study_start
    study_start = datetime.now()
    status_label.config(text="공부 시작!")

def end_study():
    global study_start, total_study_time
    if study_start:
        elapsed = datetime.now() - study_start
        total_study_time += elapsed
        study_start = None
        status_label.config(text=f"공부 종료! 총 공부 시간: {total_study_time}")
    else:
        status_label.config(text="공부를 먼저 시작하세요!")

# GUI 설정
root = tk.Tk()
root.title("공부 시간 관리 앱")
root.geometry("350x200")

start_btn = tk.Button(root, text="공부 시작", command=start_study, width=15, height=2)
start_btn.pack(pady=10)

end_btn = tk.Button(root, text="공부 종료", command=end_study, width=15, height=2)
end_btn.pack(pady=10)

status_label = tk.Label(root, text="앱을 시작하세요!", font=("Arial", 12))
status_label.pack(pady=20)

root.mainloop()
