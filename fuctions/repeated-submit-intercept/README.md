## repeat-submit-intercept

> 重复提交，指的是本次url方法**未执行完成**，对口该url方法提交重复的数据

**process**

- 每次提交，获取**Redis分布式锁**

  - 若获取锁成功，则执行提交

    后**解除**该锁，可进行**下次提交**

  - 若获取锁失败，则表示本次提交**正在进行中**，防止了重复提交

    **本次**提交后，才可以进行**下一次**提交

**knowledge**

- getServletPath()获取的是**访问**的url路径

- 若多个浏览器**窗口**执行**相同**url，浏览器会自动等待第一个窗口url请求后，再执行下一个窗口的相同url

  故出现，多个窗口测试本module，**不会出现**重复提交报警