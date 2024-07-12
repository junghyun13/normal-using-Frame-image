# normal-using-Frame-image
버튼을 누르면 이전과 다음으로 넘어가는 기본 틀 작성

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
public class LabelEX extends JFrame {
    private JFrame frame;
    private int index = 0; // 인덱스 초기화
    private JLabel lblImage; // JLabel을 인스턴스 변수로 선언
    private static final String[] IMAGES = { // 이미지 경로 문자열로 저장
        "images/bicon.jpg",
        "images/bicon1.png",
        "images/normalicon1.jpg"
    };
    public void init() {
        frame = new JFrame();
        frame.setBounds(100, 100, 450, 450);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.getContentPane().setLayout(null);

        Font font = new Font("굴림", Font.BOLD, 48);

        lblImage = new JLabel();
        lblImage.setBounds(93, 10, 256, 256);
        lblImage.setIcon(new ImageIcon(IMAGES[index]));
        frame.getContentPane().add(lblImage);

        JButton btnPrev = new JButton("이전");
        btnPrev.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                if (index > 0) { // 현재 인덱스가 0보다 크면
                    index--; // 인덱스를 감소
                } else { // 현재 인덱스가 0이면
                    index = IMAGES.length - 1; // 배열의 가장 큰 인덱스 번호로 변경}
                lblImage.setIcon(new ImageIcon(IMAGES[index])); // 버튼 누를 때마다 다음 이미지로 이동} });
        btnPrev.setFont(font);
        btnPrev.setBounds(56, 321, 141, 80);
        frame.getContentPane().add(btnPrev);
        JButton btnNext = new JButton("다음");
        btnNext.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                if (index < IMAGES.length - 1) { // 마지막 인덱스보다 작은 경우
                    index++; // 인덱스 증가
                } else { // 현 인덱스가 문자열의 길이가 -1이 되는 경우
                    index = 0; // 인덱스를 0으로 초기화(0번으로 변경)
                }
                lblImage.setIcon(new ImageIcon(IMAGES[index]));} });
        btnNext.setFont(font);
        btnNext.setBounds(245, 321, 141, 80);
        frame.getContentPane().add(btnNext);
    }
    public LabelEX() {
        init();
        frame.setVisible(true); // 프레임을 표시하도록 이동
    }
    public static void main(String[] args) {
        EventQueue.invokeLater(new Runnable() {
            public void run() {
                try {
                    LabelEX window = new LabelEX();
                    window.frame.setVisible(true);
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
        }); } }
