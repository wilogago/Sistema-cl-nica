import java.util.ArrayList;
import java.util.Scanner;

public class SistemaClinica {

    static class Paciente {
        String nome;
        String telefone;

        Paciente(String nome, String telefone) {
            this.nome = nome;
            this.telefone = telefone;
        }
    }

    static class Consulta {
        String nomePaciente;
        String medico;
        String horario;

        Consulta(String nomePaciente, String medico, String horario) {
            this.nomePaciente = nomePaciente;
            this.medico = medico;
            this.horario = horario;
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        ArrayList<Paciente> pacientes = new ArrayList<>();
        ArrayList<String> medicos = new ArrayList<>();
        ArrayList<Consulta> consultas = new ArrayList<>();

        medicos.add("Dra. Ana - Pediatria");
        medicos.add("Dr. Carlos - Ortopedia");
        medicos.add("Dr. Rafael - Clínica Geral");

        int opcao = -1;

        while (opcao != 0) {
            System.out.println("\n=== SISTEMA DE CLINICA ===");
            System.out.println("1 - Cadastrar paciente");
            System.out.println("2 - Listar pacientes");
            System.out.println("3 - Cadastrar medico");
            System.out.println("4 - Listar medicos");
            System.out.println("5 - Agendar consulta");
            System.out.println("6 - Listar consultas");
            System.out.println("7 - Cancelar consulta");
            System.out.println("0 - Sair");
            System.out.print("Escolha uma opcao: ");

            if (!sc.hasNextInt()) {
                System.out.println("Digite apenas um numero valido.");
                sc.nextLine();
                continue;
            }

            opcao = sc.nextInt();
            sc.nextLine();

            if (opcao == 1) {
                System.out.print("Nome do paciente: ");
                String nome = sc.nextLine().trim();

                System.out.print("Telefone do paciente: ");
                String telefone = sc.nextLine().trim();

                if (nome.isEmpty() || telefone.isEmpty()) {
                    System.out.println("Nome e telefone sao obrigatorios.");
                } else {
                    pacientes.add(new Paciente(nome, telefone));
                    System.out.println("Paciente cadastrado com sucesso!");
                }

            } else if (opcao == 2) {
                System.out.println("\n--- Pacientes cadastrados ---");
                if (pacientes.isEmpty()) {
                    System.out.println("Nenhum paciente cadastrado.");
                } else {
                    for (int i = 0; i < pacientes.size(); i++) {
                        Paciente p = pacientes.get(i);
                        System.out.println((i + 1) + ". Nome: " + p.nome + " | Telefone: " + p.telefone);
                    }
                }

            } else if (opcao == 3) {
                System.out.print("Nome e especialidade (ex: Dra. Julia - Cardiologia): ");
                String medico = sc.nextLine().trim();

                if (medico.isEmpty()) {
                    System.out.println("Informe os dados do medico.");
                } else {
                    medicos.add(medico);
                    System.out.println("Medico cadastrado com sucesso!");
                }

            } else if (opcao == 4) {
                System.out.println("\n--- Medicos cadastrados ---");
                if (medicos.isEmpty()) {
                    System.out.println("Nenhum medico cadastrado.");
                } else {
                    for (int i = 0; i < medicos.size(); i++) {
                        System.out.println((i + 1) + ". " + medicos.get(i));
                    }
                }

            } else if (opcao == 5) {
                if (pacientes.isEmpty()) {
                    System.out.println("Cadastre pelo menos um paciente antes de agendar.");
                    continue;
                }
                if (medicos.isEmpty()) {
                    System.out.println("Cadastre pelo menos um medico antes de agendar.");
                    continue;
                }

                System.out.println("\nEscolha o paciente:");
                for (int i = 0; i < pacientes.size(); i++) {
                    System.out.println((i + 1) + ". " + pacientes.get(i).nome);
                }
                System.out.print("Numero do paciente: ");
                int idxPaciente = sc.nextInt() - 1;
                sc.nextLine();

                System.out.println("\nEscolha o medico:");
                for (int i = 0; i < medicos.size(); i++) {
                    System.out.println((i + 1) + ". " + medicos.get(i));
                }
                System.out.print("Numero do medico: ");
                int idxMedico = sc.nextInt() - 1;
                sc.nextLine();

                System.out.print("Data e horario (ex: 26/11 as 14h): ");
                String horario = sc.nextLine().trim();

                if (idxPaciente >= 0 && idxPaciente < pacientes.size()
                        && idxMedico >= 0 && idxMedico < medicos.size()
                        && !horario.isEmpty()) {
                    String nomePac = pacientes.get(idxPaciente).nome;
                    String nomeMed = medicos.get(idxMedico);
                    consultas.add(new Consulta(nomePac, nomeMed, horario));
                    System.out.println("Consulta agendada com sucesso!");
                } else {
                    System.out.println("Dados invalidos. Tente novamente.");
                }

            } else if (opcao == 6) {
                System.out.println("\n--- Consultas agendadas ---");
                if (consultas.isEmpty()) {
                    System.out.println("Nenhuma consulta agendada.");
                } else {
                    for (int i = 0; i < consultas.size(); i++) {
                        Consulta c = consultas.get(i);
                        System.out.println((i + 1) + ". Paciente: " + c.nomePaciente
                                + " | Medico: " + c.medico
                                + " | Horario: " + c.horario);
                    }
                }

            } else if (opcao == 7) {
                if (consultas.isEmpty()) {
                    System.out.println("Nenhuma consulta para cancelar.");
                    continue;
                }

                System.out.println("\n--- Escolha a consulta para cancelar ---");
                for (int i = 0; i < consultas.size(); i++) {
                    Consulta c = consultas.get(i);
                    System.out.println((i + 1) + ". Paciente: " + c.nomePaciente
                            + " | Medico: " + c.medico
                            + " | Horario: " + c.horario);
                }

                System.out.print("Numero da consulta (0 para voltar): ");
                if (!sc.hasNextInt()) {
                    System.out.println("Digite um numero valido.");
                    sc.nextLine();
                    continue;
                }

                int idxCancelar = sc.nextInt() - 1;
                sc.nextLine();

                if (idxCancelar == -1) {
                    System.out.println("Cancelamento abortado.");
                } else if (idxCancelar >= 0 && idxCancelar < consultas.size()) {
                    Consulta removida = consultas.remove(idxCancelar);
                    System.out.println("Consulta cancelada: " + removida.nomePaciente
                            + " com " + removida.medico + " (" + removida.horario + ")");
                } else {
                    System.out.println("Numero de consulta invalido.");
                }

            } else if (opcao == 0) {
                System.out.println("Encerrando o sistema...");
            } else {
                System.out.println("Opcao invalida.");
            }
        }

        sc.close();
    }
}
