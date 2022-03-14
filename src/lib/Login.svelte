<script lang="ts">
  import { navigate } from "svelte-routing";
  import { createForm } from "felte";
  import user from "../store";
  interface Value {
    username: string;
    password: string;
  }
  const mockLogin = async (value: Value): Promise<void> => {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        user.set({ username: value.username });
        navigate("/", { replace: true });
        resolve();
      }, 1000);
    });
  };

  const { form } = createForm({
    onSubmit: async (values: Value): Promise<void> => {
      await mockLogin(values);
    },
  });
</script>

<div>
  <form use:form>
    <div><input type="text" name="username" /></div>
    <div><input type="password" name="password" /></div>
    <div><input class="animate-bounce" type="submit" value="submit" /></div>
  </form>
</div>
