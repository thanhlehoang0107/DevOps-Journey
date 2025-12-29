# 🛡️ Module 4.2: Infrastructure Security

> **Secure Infrastructure** - Hardening, compliance, và security monitoring.

---

## 🎯 Learning Objectives

- ✅ Cloud security best practices
- ✅ Network security
- ✅ Secrets management
- ✅ Compliance frameworks
- ✅ Security monitoring
- ✅ Incident response

---

## 📚 Content

### 1. Secrets Management

```bash
# HashiCorp Vault
vault kv put secret/myapp db_password=secret123
vault kv get secret/myapp

# AWS Secrets Manager
aws secretsmanager create-secret \
  --name MySecret \
  --secret-string '{"password":"secret123"}'
```

### 2. AWS Security

```bash
# Enable GuardDuty
aws guardduty create-detector --enable

# Security Hub
aws securityhub enable-security-hub

# Config Rules
aws configservice put-config-rule --config-rule file://rule.json
```

### 3. CIS Benchmarks

- OS hardening
- SSH configuration
- Firewall rules
- Audit logging

### 4. Compliance

```yaml
# InSpec
control 'ssh-config' do
  impact 1.0
  title 'SSH configuration'
  
  describe sshd_config do
    its('PermitRootLogin') { should eq 'no' }
    its('PasswordAuthentication') { should eq 'no' }
  end
end
```

---

## 📝 Module Files

- [LABS.md](./LABS.md) | [QUIZ.md](./QUIZ.md) | [EXERCISES.md](./EXERCISES.md)
